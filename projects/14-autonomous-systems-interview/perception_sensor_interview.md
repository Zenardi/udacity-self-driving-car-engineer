# Perception/Sensor Engineer — Autonomous Systems Interview

**Role:** Perception / Sensor Engineer  
**Company context:** Bosch Automotive (ADAS & Autonomous Driving division)  
**Nanodegree:** Udacity Self-Driving Car Engineer  

- [Perception/Sensor Engineer — Autonomous Systems Interview](#perceptionsensor-engineer--autonomous-systems-interview)
  - [Table of Contents](#table-of-contents)
  - [Required Question — Recent Project](#required-question--recent-project)
    - [Answer](#answer)
    - [Follow-up question](#follow-up-question)
  - [Q1 — Camera, LiDAR and Radar: Advantages, Disadvantages \& Sensor Fusion Strategy](#q1--camera-lidar-and-radar-advantages-disadvantages--sensor-fusion-strategy)
    - [Answer](#answer-1)
      - [Sensor comparison](#sensor-comparison)
      - [Recommended sensor suite](#recommended-sensor-suite)
      - [Fusion architecture](#fusion-architecture)
    - [Follow-up question](#follow-up-question-1)
  - [Q2 — The Kalman Filter: Process, Limitations and Improvements](#q2--the-kalman-filter-process-limitations-and-improvements)
    - [Answer](#answer-2)
      - [The Kalman Filter in a nutshell](#the-kalman-filter-in-a-nutshell)
        - [1. Predict step](#1-predict-step)
        - [2. Update step](#2-update-step)
      - [Where the basic KF is insufficient](#where-the-basic-kf-is-insufficient)
      - [Improvements](#improvements)
    - [Follow-up question](#follow-up-question-2)
  - [Q3 \[Code\] — Implementing an Extended Kalman Filter](#q3-code--implementing-an-extended-kalman-filter)
    - [Answer](#answer-3)
      - [State vector](#state-vector)
      - [Steps](#steps)
      - [C++ Implementation](#c-implementation)
      - [Key implementation notes](#key-implementation-notes)
    - [Follow-up question](#follow-up-question-3)


---

## Table of Contents

1. [Required Question — Recent Project](#required-question--recent-project)
2. [Q1 — Camera, LiDAR and Radar: Advantages, Disadvantages & Sensor Fusion Strategy](#q1--camera-lidar-and-radar-advantages-disadvantages--sensor-fusion-strategy)
3. [Q2 — The Kalman Filter: Process, Limitations and Improvements](#q2--the-kalman-filter-process-limitations-and-improvements)
4. [Q3 [Code] — Implementing an Extended Kalman Filter](#q3-code--implementing-an-extended-kalman-filter)

---

## Required Question — Recent Project

> **"Explain a recent project you've worked on. Why did you choose this project? What difficulties did you run into that you did not expect, and how did you solve them?"**

### Answer

At Bosch I was part of the team developing the **Radar-Based Multi-Object Tracking pipeline** for Bosch's 77 GHz long-range radar sensor (LRR4), targeted at production Adaptive Cruise Control (ACC) and Autonomous Emergency Braking (AEB) systems.

**Why this project?**  
Radar is the backbone of highway-speed ADAS. Unlike cameras, it is unaffected by glare, fog, or rain, and unlike LiDAR it is cost-effective enough for high-volume passenger cars. Building a robust tracker on top of raw radar returns — turning noisy point clusters into tracked objects with stable IDs, velocity, and acceleration estimates — is one of the most impactful things a perception engineer can do.

**Pipeline overview:**

```
Raw FMCW radar detections
        │
        ▼
  CFAR Filtering          (Constant False Alarm Rate — removes clutter)
        │
        ▼
  Clustering (DBSCAN)     (groups individual detections into candidate objects)
        │
        ▼
  Data Association        (nearest-neighbour / Hungarian algorithm)
        │
        ▼
  EKF Tracker             (one filter per track; state: [x, y, vx, vy])
        │
        ▼
  Track Management        (birth / confirmation / deletion logic)
        │
        ▼
  CAN bus output          → ACC controller, AEB controller
```

**Unexpected difficulty 1 — Ghost tracks at highway speeds**  
At speeds above 120 km/h, multi-path reflections off the road surface created stable, ghost detections that the tracker would happily promote to confirmed tracks. These were indistinguishable from real objects using position and velocity alone.

*Solution:* We added a **radar cross-section (RCS) consistency check** across frames and a minimum elevation constraint derived from the beam pattern model. Ghost tracks had inconsistent RCS signatures, so a short-history RCS variance filter suppressed them before track confirmation.

**Unexpected difficulty 2 — Sensor–vehicle coordinate frame drift**  
Mounting tolerances meant the sensor boresight could be off by ±1.5° in azimuth, which at 150 m range produces a 4 m lateral error — enough to assign a tracked car to the wrong lane.

*Solution:* We implemented an **online extrinsic calibration** routine: using stationary infrastructure detections during straight-line driving to continuously estimate and correct the mounting angle offset, feeding a rolling average into the coordinate transform.

---

### Follow-up question

> **"You mentioned ghost tracks from multi-path reflections. Could machine-learning help here, and why might you still prefer a classical signal-processing approach in a production vehicle?"**

**Answer:**  
Yes — a learned classifier (e.g., a small 1D CNN over the FMCW range-Doppler map) could learn to separate ghost returns from real targets with high recall. However, in a production AEB system, the key concern is **explainability and certification under ISO 26262 ASIL-B/C**. A classical CFAR + RCS-variance filter has a deterministic, mathematically bounded false-positive rate that can be proven at the component level. A neural network would require extensive corner-case coverage data, an ASIL-decomposition argument, and potentially runtime monitors — significantly increasing validation cost and time-to-market. The pragmatic Bosch approach is to use learned components for non-safety-critical perception (scene classification, sign reading) while keeping the safety-critical tracking chain classical and certifiable.

---

## Q1 — Camera, LiDAR and Radar: Advantages, Disadvantages & Sensor Fusion Strategy

> **"What are some of the advantages & disadvantages of cameras, LiDAR and radar? What combination of these (and other sensors) would you use to ensure appropriate and accurate perception of the environment?"**

### Answer

#### Sensor comparison

| Property | Camera | LiDAR | Radar |
|---|---|---|---|
| **Spatial resolution** | Very high (megapixels) | High (dense point cloud) | Low (sparse, ~0.1° azimuth) |
| **Range** | Medium (~100 m practical) | Medium–high (~200 m) | Very high (300+ m long-range) |
| **Velocity measurement** | Indirect (optical flow) | Indirect (frame diff) | **Direct (Doppler)** |
| **Semantic richness** | **Very high** (texture, colour, text) | Low (geometry only) | Very low |
| **Weather robustness** | Poor (fog, rain, glare) | Moderate (rain degrades) | **Excellent** |
| **Night performance** | Poor (needs illumination) | Good (active sensor) | **Excellent** |
| **Cost (2024)** | Low | High (mechanical) / Med (solid-state) | Low–Medium |
| **3D localisation** | Requires stereo/depth net | **Native 3D** | Native range + azimuth |
| **False alarm source** | Lighting, shadows, occlusion | Dust, glass, retroreflectors | Metal clutter, multipath |

#### Recommended sensor suite

For a Level 3+ highway autonomous system (the target for Bosch's ADAS roadmap):

```
             ┌──────────────────────────────────┐
             │       Sensor Suite Layout         │
             └──────────────────────────────────┘

  [LRR front]   [camera front]   [LRR front]
       \              |               /
        \             |              /
         ●────────────●────────────●    ← front sensor cluster
         
  [SRR FL]  [camera FL/FR]  [SRR FR]   ← corner radars + surround cams
  
  [SRR RL]  [LiDAR roof]   [SRR RR]   ← rear corners + roof LiDAR
  
         ●────────────●────────────●    ← rear sensor cluster
  [LRR rear]  [camera rear]  [LRR rear]
```

- **2× 77 GHz long-range radar** (front/rear): primary velocity & range source for ACC/AEB  
- **4× short-range corner radar**: low-speed cross-traffic, parking  
- **1× roof-mounted solid-state LiDAR** (e.g., Bosch BMI088): high-fidelity 3D geometry for object shape + free-space  
- **6× cameras** (fisheye surround + forward telephoto): semantic classification, lane detection, traffic sign recognition  
- **IMU + GNSS**: ego-motion reference for tracker prediction step  

#### Fusion architecture

A **late fusion / track-level fusion** architecture is used at Bosch for ACC because each sensor already provides a track list with associated uncertainty covariances. These are merged with an **Unscented Kalman Filter** fusion layer, which weights each sensor's contribution by its inverse covariance at each time step. This provides graceful degradation — if the camera fails in fog, the radar tracks continue uninterrupted.

---

### Follow-up question

> **"You chose late fusion. Under what circumstances would you prefer early (raw data) fusion instead?"**

**Answer:**  
Early fusion — e.g., concatenating camera image features with LiDAR point-cloud features inside a neural network before detection — can be superior when sensors are **tightly time-synchronised** and the objects of interest have distinguishing features that span modalities (for example, pedestrian body shape from LiDAR + thermal signature from a far-infrared camera). In practice, early fusion is used in robotics research and Level 4/5 robo-taxi development (Waymo, Cruise) where compute budgets are larger and ASIL constraints are less restrictive. For Bosch's production ADAS with strict latency budgets (<50 ms end-to-end) and ASIL-B requirements, late fusion remains the preferred choice because each sensing branch is independently validatable.

---

## Q2 — The Kalman Filter: Process, Limitations and Improvements

> **"Describe the overall process of how a basic Kalman Filter works. Where might a basic Kalman Filter be less than sufficient? How can you improve the basic algorithm to improve performance in such a situation?"**

### Answer

#### The Kalman Filter in a nutshell

The Kalman Filter (KF) is a **recursive Bayesian estimator** for linear systems with Gaussian noise. It maintains a belief over the system state as a Gaussian:

```
Belief at time t:  p(xₜ | z₁…zₜ) = 𝒩(μₜ, Σₜ)
```

The filter cycles through two steps:

##### 1. Predict step

Using the motion model `F` and process noise `Q`:

```
μ̄ₜ = F · μₜ₋₁ + B · uₜ          (state prediction)
Σ̄ₜ = F · Σₜ₋₁ · Fᵀ + Q          (covariance prediction)
```

- `F` — state transition matrix (e.g., constant-velocity model)
- `B · uₜ` — optional control input (odometry, IMU)
- `Q` — process noise covariance (models unmodelled accelerations)

##### 2. Update step

Using measurement `zₜ`, observation matrix `H`, and measurement noise `R`:

```
yₜ  = zₜ - H · μ̄ₜ               (innovation / residual)
Sₜ  = H · Σ̄ₜ · Hᵀ + R           (innovation covariance)
Kₜ  = Σ̄ₜ · Hᵀ · Sₜ⁻¹            (Kalman gain)

μₜ  = μ̄ₜ + Kₜ · yₜ              (posterior mean)
Σₜ  = (I - Kₜ · H) · Σ̄ₜ        (posterior covariance)
```

The Kalman gain `K` acts as a **trust knob**: when `R` is small (precise sensor), `K` is large and the measurement dominates; when `Q` is small (precise model), the prediction dominates.

#### Where the basic KF is insufficient

The standard KF assumes:

1. **Linear dynamics** — `F` is a matrix  
2. **Linear observation model** — `H` is a matrix  
3. **Gaussian noise** throughout  

In vehicle perception, both assumptions routinely break:

| Scenario | Non-linearity |
|---|---|
| Radar measures range `r` and bearing `θ`, not Cartesian `(x,y)` | Observation model `h(x) = [√(x²+y²), atan2(y,x)]` is nonlinear |
| Vehicle turning at constant yaw rate (CTRV model) | State transition is nonlinear: `x' = x + v/ω · (sin(ψ+ωΔt) - sin(ψ))` |
| Pedestrian sudden direction changes | Motion model error is non-Gaussian (heavy-tailed) |

#### Improvements

1. **Extended Kalman Filter (EKF):** Linearises nonlinear functions via a first-order Taylor expansion (Jacobian). Efficient, widely used in production ADAS. See Q3 for full implementation details.

2. **Unscented Kalman Filter (UKF):** Uses deterministic sigma points to capture higher-order moments without computing Jacobians. More accurate for highly nonlinear systems, especially the CTRV motion model.

3. **Particle Filter:** Represents the posterior with a set of weighted samples — handles multimodal, non-Gaussian distributions. Computationally expensive; used in global localisation (Monte Carlo Localisation) rather than per-object tracking.

---

### Follow-up question

> **"In your Bosch radar tracker, which motion model did you use, and why did you choose it over the constant-velocity model?"**

**Answer:**  
We used a **Constant Turn-Rate and Velocity (CTRV)** model for the EKF. The CV model predicts a straight-line trajectory in the next step, which is adequate on highways but introduces large prediction errors (and hence missed associations) when a target vehicle is changing lanes or rounding an on-ramp. The CTRV model adds yaw `ψ` and yaw rate `ψ̇` to the state vector `[x, y, v, ψ, ψ̇]`, correctly predicting a circular arc. The cost is that the CTRV transition function is nonlinear even for the state (not just the observation), which is why we used an UKF for that project variant — avoiding the Jacobian of the CTRV function, which has a singularity when `ψ̇ ≈ 0`.

---

## Q3 [Code] — Implementing an Extended Kalman Filter

> **"Explain the steps behind how an Extended Kalman Filter is implemented." [Code]**

### Answer

The **Extended Kalman Filter** handles nonlinear systems by linearising around the current state estimate at each time step using the Jacobian of the nonlinear function.

#### State vector

For the Bosch radar tracker we track each object with:

```
x = [px, py, vx, vy]ᵀ
```

where `(px, py)` is position and `(vx, vy)` is velocity in the sensor's Cartesian frame.

#### Steps

**1. Initialise** the state `x` and covariance `P` from the first measurement.

**2. Predict** using the linear constant-velocity motion model:

```
F = | 1  0  Δt  0  |       Q models random acceleration noise
    | 0  1   0  Δt |
    | 0  0   1   0 |
    | 0  0   0   1 |
```

**3. Update** using the radar measurement `z = [ρ, φ, ρ̇]ᵀ` (range, bearing, range-rate):
- The observation function `h(x)` is **nonlinear** — compute it directly.
- Replace `H` with the **Jacobian** `Hⱼ` (linearisation).
- Proceed with the standard KF update equations using `Hⱼ`.

#### C++ Implementation

```cpp
#include <cmath>
#include <Eigen/Dense>

using Eigen::MatrixXd;
using Eigen::VectorXd;

// ─── Jacobian of radar measurement h(x) ─────────────────────────────────────
MatrixXd ComputeJacobian(const VectorXd& x) {
    MatrixXd Hj(3, 4);
    Hj.setZero();

    const double px = x(0), py = x(1), vx = x(2), vy = x(3);
    const double rho2    = px*px + py*py;
    const double rho     = std::sqrt(rho2);
    const double rho3_2  = rho2 * rho;  // rho^3 (= rho * rho^2)

    // Guard against division by zero
    if (rho < 1e-4) return Hj;

    Hj(0, 0) =  px / rho;
    Hj(0, 1) =  py / rho;

    Hj(1, 0) = -py / rho2;
    Hj(1, 1) =  px / rho2;

    Hj(2, 0) =  py * (vx*py - vy*px) / rho3_2;
    Hj(2, 1) =  px * (vy*px - vx*py) / rho3_2;
    Hj(2, 2) =  px / rho;
    Hj(2, 3) =  py / rho;

    return Hj;
}

// ─── EKF class ───────────────────────────────────────────────────────────────
class ExtendedKalmanFilter {
public:
    VectorXd x_;   // state [px, py, vx, vy]
    MatrixXd P_;   // state covariance
    MatrixXd F_;   // state transition matrix
    MatrixXd Q_;   // process noise covariance
    MatrixXd R_radar_;  // radar measurement noise [ρ, φ, ρ̇]

    // ── Predict ──────────────────────────────────────────────────────────────
    void Predict(double dt) {
        // Update F with current dt
        F_(0, 2) = dt;
        F_(1, 3) = dt;

        // Build Q using noise_ax=9, noise_ay=9 (m²/s⁴) — typical for cars
        const double noise_ax = 9.0, noise_ay = 9.0;
        const double dt2 = dt * dt;
        const double dt3 = dt2 * dt;
        const double dt4 = dt3 * dt;

        Q_ << dt4/4*noise_ax,           0, dt3/2*noise_ax,           0,
                           0, dt4/4*noise_ay,           0, dt3/2*noise_ay,
              dt3/2*noise_ax,           0,   dt2*noise_ax,           0,
                           0, dt3/2*noise_ay,           0,   dt2*noise_ay;

        x_ = F_ * x_;
        P_ = F_ * P_ * F_.transpose() + Q_;
    }

    // ── Update with radar measurement (nonlinear h → use Jacobian) ───────────
    void UpdateRadar(const VectorXd& z) {
        // 1. Compute h(x): map state to radar measurement space
        const double px = x_(0), py = x_(1), vx = x_(2), vy = x_(3);
        const double rho  = std::sqrt(px*px + py*py);
        const double phi  = std::atan2(py, px);
        const double rhod = (rho > 1e-4) ? (px*vx + py*vy) / rho : 0.0;

        VectorXd z_pred(3);
        z_pred << rho, phi, rhod;

        // 2. Innovation y — normalise the bearing angle to [-π, π]
        VectorXd y = z - z_pred;
        while (y(1) >  M_PI) y(1) -= 2.0 * M_PI;
        while (y(1) < -M_PI) y(1) += 2.0 * M_PI;

        // 3. Jacobian Hj replaces H in all KF update equations
        MatrixXd Hj = ComputeJacobian(x_);

        // 4. Standard KF update with Hj
        MatrixXd S = Hj * P_ * Hj.transpose() + R_radar_;
        MatrixXd K = P_ * Hj.transpose() * S.inverse();

        x_ = x_ + K * y;
        P_ = (MatrixXd::Identity(4, 4) - K * Hj) * P_;
    }
};
```

#### Key implementation notes

| Step | Detail |
|---|---|
| **Jacobian guard** | If `ρ < 1e-4` (object at origin), `Hⱼ` is undefined — return zero matrix or skip update |
| **Bearing normalisation** | The innovation `y(1)` (bearing residual) must be wrapped to `[-π, π]` to avoid discontinuity at ±180° |
| **First measurement init** | On the first radar measurement, convert `(ρ, φ)` to `(px, py)` using trigonometry; set `vx=vy=0` as initial guess |
| **Camera vs radar update** | For camera detections use the linear `H` matrix and standard KF update; only radar requires the EKF path |

---

### Follow-up question

> **"Why do we normalize the bearing angle in the innovation step, and what would happen if we didn't?"**

**Answer:**  
Angles wrap around at ±π. Suppose the predicted bearing is `φ̄ = 3.1 rad` (~178°) and the measured bearing is `z = -3.1 rad` (~-178°). Mathematically these are only 0.08 rad apart, but without normalisation the raw innovation would be `z - φ̄ ≈ -6.28 rad`, which is an enormous apparent error. The Kalman gain would then pull the state estimate wildly in the wrong direction, corrupting the track. Normalising the innovation to `[-π, π]` ensures the filter always uses the **shortest angular path**, keeping the update numerically stable and physically correct.


