# Lidar Selection Criteria

> Part of: **The Lidar Sensor**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=JMq-Dl7T9l8)

## Summary

**Lidar Sensor Selection Criteria**

This README file provides an overview of key concepts and selection criteria for comparing Lidar sensors in the automotive sector.

### Key Concepts

* **Lidar Technology Evolution**: Lidar technology is rapidly changing with incremental improvements and major breakthroughs announced regularly, making it challenging to compare technologies.
* **Selection Criteria**: A set of criteria can be used to generate a side-by-side comparison of Lidar sensors, enabling informed selection for development projects.
* **Range Images**: Understanding the concept behind range images, which are 2D representations of 3D scenes, is crucial when working with lidar data.
* **Intensity, Inclination, and Azimuth Angle**: Familiarity with these key parameters is essential for interpreting lidar data.

### Practical Notes

* When comparing Lidar sensors, consider factors such as:
	+ Data resolution
	+ Field of view
	+ Range accuracy
	+ Power consumption
	+ Cost
* Be prepared to work with lidar data in the next chapter, including understanding range images and interpreting intensity, inclination, and azimuth angle values.
* Familiarize yourself with programming languages and libraries used for working with lidar data.

## Transcript

Now at this point, you have an overview of the available Lidar technologies currently available in the automotive sector today. Also, you are aware of the fact that Lidar technology undergoes rapid changes with incremental improvements here and there, and even sometimes with major technological breakthroughs being announced almost on a monthly basis. With such rapid development, it's often difficult to compare technologies to each other, and as a next step, select a specific sensor for one of your development projects. In this section, we will therefore discuss a number of selection criteria which can be used to generate a side-by-side comparison of Lidar sensors. Now this chapter has provided you with everything you need to know in order to properly work with lidar data.

Be it from the way more data set or from other sources, such as the well-known pity data set for example. When we start working with lidar data in the next chapter, you will have no trouble now understanding the concept behind range images, intensity, inclination or azimuth angle, and better get your coding gear ready now, because you are about to write some programs in the next chapter. See you there as soon as possible.

## Additional Content

## LiDAR Selection Criteria
### Eye Safety

As LiDAR sensors shoot laser beams into the atmosphere, it must be ensured that they are not harmful to the naked eye. As you have seen in the previous section, there are three factors which influence eye safety, which are (a) emitter power, (b) pulse duration and (c) light frequency. Eye safety standards categorize LiDAR sensors based on their output optical power level. For automotive applications, LiDAR sensors must either be classified as a Class 1 or Class 1M laser safety level. 

### Field of View (FOV)

Autonomous vehicles must perceive their environment in a 360° circumference. Also, it must be ensured that the entire driving corridor with respect to the vehicle's height is observed. Both of these observations result in two parameters, which are the horizontal field-of-view (HFOV) and the vertical field-of-view (VFOV) of a sensor. If we consider the classic Velodyne HDL 64E LiDAR, the HFOV is at 360° and the HFOV is at 26.9°, which, from a roof-mounted position, is sufficient to scan the environment from close to far range. Instead of using a single sensor though, multiple sensors with overlapping FOV may be used to complement each other. In Waymo vehicles, for example, the three LiDAR sensors at the front with a comparatively narrow but overlapping HFOV are used to observe the front and side of the vehicle at close-range. 

### Angular resolution

A critical parameter which controls the density of the point-cloud is the angular resolution of a LiDAR sensor. It defines the number of laser beams the sensor can project into its FOV. For the Velodyne HDL 64E with its 64 individual beams, the vertical resolution is at $\approx 0.4\degree$ while the horizontal resolution is at $\approx 0.8\degree$ based on the number of scans over a full rotation of the mirror. In order to track features such as curb-sides or a bicycle frame, a very fine angular resolution both in the horizontal and vertical direction are needed. 

### Number of points

Based on the angular resolution and the field-of-view, the number of 3d points can be calculated which the sensor returns over a full scanning cycle. 
### Frame rate

The frame rate of a LiDAR sensor provides the number of full sweeps over both the HFOV and the VFOF. In case of the Velodyne HDL 64E, the frame rate can be adjusted between 5Hz and 20Hz, depending on the requirements of the application and on the number of points that the respective system can handle performance-wise. Other than with the frame rate of a camera though, LiDAR measurements might not be performed at the same time instant. As the sensor sweeps across the scene, moving objects change their position, which results in smeared and potentially elongated objects, which have to be corrected before processing them. For solid-state LiDAR sensors however, this is not the case.
### Maximum range

Depending on the relative speed between LiDAR sensor and targets, you need to decide on the maximum range at which objects can still be detected with a sufficiently high probability. In LiDAR data sheets, you will find information on the maximum range of the respective sensor. However, you can not expect that the type of target you are looking for will actually be detected in a stable manner at maximum range. The reason for this can be explained by the way target measurements are performed by the LiDAR manufacturer: When assessing the range scanning capabilities of a sensor, a set of known targets with specific reflectance parameters will be used. Typically, a reflector is characterized as "poor", when its reflectance is below 10% and as "good", when reflectance exceeds 90%. In most cases, the target reflectance which has been used to define the maximum range will be specified in the data sheet. 

### Range resolution

Based on factors such as return signal strength, receiver sensitivity and the resolution of the timing device, the range resolution provides the smallest change in target distance, that is still perceivable by the LiDAR system. 

Other common parameters are e.g. "Pulse Repetition Rate (PRR) or Frequency (PRF)", the "Peak Power" and "Average Power" as well as the "Wavelength" of the laser beam.

## Outro

[Watch on YouTube](https://www.youtube.com/watch?v=fZIeGABPHtM)