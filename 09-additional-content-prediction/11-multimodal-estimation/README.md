# Multimodal Estimation

> Part of: **Prediction**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=u1Tmt0Qdlgk)

## Summary

**Multimodal Estimation Algorithms for Autonomous Systems**
===========================================================

This project explores the concept of multimodal estimation algorithms, specifically Autonomous Multiple Model (AMM) estimation. AMM is a simple approach to estimating the probability of different behaviors in an autonomous system.

**Key Concepts**
---------------

* **Multimodal estimation**: A technique used to estimate multiple possible behaviors or outcomes in an autonomous system.
* **Autonomous Multiple Model (AMM)**: A specific type of multimodal estimation algorithm that estimates the probability of each behavior based on observations and previous probabilities.
* **Process models**: Mathematical representations of different behaviors or maneuvers, such as going straight or turning right.
* **Gaussian uncertainty**: A statistical model used to represent the uncertainty associated with process models.
* **Likelihood ratio**: The ratio of the likelihoods of an observation given each behavior, used to update the probabilities of each behavior.

**Practical Notes**
------------------

The AMM algorithm can be implemented using the following steps:

1. Define the number of process models (M) and their corresponding variables (mu).
2. Initialize the probabilities of each behavior based on previous observations.
3. Run each process model for one step starting from the current state, generating expected states at time k.
4. Compute the likelihoods of the observation given each behavior using the expected states.
5. Update the probabilities of each behavior using the likelihood ratio equation:
```
p(model I at timestep K) = p(model I at timestep K-1) \* L(observation at time K for model I) / (sum(p(model J at timestep K-1) \* L(observation at time K for model J)) for all J)
```
Note that this equation normalizes the probabilities so that they sum to one.

## Transcript

<v English>We have talked about individual process models but we haven&#39;t yet talked</v> <v English>about how to maintain some beliefs about which behavior the driver intends to perform.</v> <v English>This is the role of multimodal estimation algorithms.</v> <v English>A simple approach to multimodal estimation is called</v> <v English>autonomous multiple model estimation or AMM.</v> <v English>While describing AMM, I will use</v> <v English>the same notation that is used in a paper which I will link to later.</v> <v English>The variable M represents the number of process models or</v> <v English>behaviors and each variable mu represents the probability of behavior.</v> <v English>To understand how these probabilities are computed,</v> <v English>let&#39;s go back to our T intersection example.</v> <v English>Let&#39;s say we have two process models here.</v> <v English>One to go straight and one to turn right and they both have Gaussian uncertainty.</v> <v English>Let&#39;s say that we observe this state for the vehicle at time k minus one and we observe</v> <v English>this state for the vehicle at time k. In order to</v> <v English>compute the new probabilities for the behaviors based on the new observation,</v> <v English>we will run our two process models for</v> <v English>one step starting from the state at time k minus one.</v> <v English>When we do this,</v> <v English>we get these two expected states for time k. If we just look at what</v> <v English>the distribution on the vehicle&#39;s s coordinate looks</v> <v English>like for the two expected states, this is what we see.</v> <v English>Where the red curve gives the probability density function of S for turning right,</v> <v English>the blue curve represents going straight</v> <v English>and the observation at timestep k is somewhere here.</v> <v English>We can see that this observation is substantially more</v> <v English>consistent with turn right than it is with go straight.</v> <v English>This is measured by the likelihood of the observation as</v> <v English>for each model and the probability of</v> <v English>each behavior is a function of these likelihoods</v> <v English>and of the probabilities computed in the previous timestep.</v> <v English>The important quantity for the AMM is</v> <v English>the ratio of these likelihoods after they get multiplied by the previous probability.</v> <v English>The equation ends up looking like this,</v> <v English>where this term is the probability of model I</v> <v English>at timestep K. This term is the probability of</v> <v English>model I at timestep K minus one and</v> <v English>this L term is the likelihood of the observation at time K for that model.</v> <v English>The denominator just serves to normalize our probabilities so that they all sum to one.</v> <v English>M, in this situation would be two since we are only considering two maneuvers.</v>
