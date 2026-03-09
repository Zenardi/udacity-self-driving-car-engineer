# LiDAR vs. Radar vs. Cameras

> Part of: **The Lidar Sensor**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=HP8YL4yxkXA)

## Summary

**Lidar Sensor Debate and Autonomous Vehicles**
=====================================================

This lesson discusses the ongoing debate about the use of Lidar sensors in autonomous vehicles, with companies like Waymo relying heavily on them and others, such as Tesla, questioning their necessity.

### Key Concepts

* **Lidar sensor**: a type of sensor that uses laser light to create high-resolution 3D images of the environment.
* **Autonomous vehicle levels**: there are five levels of autonomous driving, with level 5 being fully autonomous. The lesson covers the basics of these levels.
* **Sensor comparison**: the lesson introduces parameters used in automotive practice to compare sensors such as cameras, Lidar sensors, and radar.
* **Lidar vs. Radar**: the debate between using Lidar sensors or radar for object detection in autonomous vehicles.

### Practical Notes

The lesson emphasizes the importance of selecting the right sensors for autonomous vehicles based on performance and reliability rather than cost. It also highlights the current state of Lidar sensor development, with many companies working to reduce costs and improve performance. The next chapter will involve writing code using open datasets and extracting sensor information from them.

**Example Code**
```python
# Example code snippet (not provided in the lesson)
import pandas as pd

# Load dataset
data = pd.read_csv('sensor_data.csv')

# Extract Lidar sensor data
lidar_data = data['Lidar_X'], data['Lidar_Y'], data['Lidar_Z']
```
Note: The example code is not part of the original transcript, but rather a hypothetical representation of what might be covered in the next chapter.

## Transcript

For quite some time now, there has been a heavy dispute going on in the automotive community about the appropriate role of the Lidar sensor. In companies such as Waymo, on one end of the spectrum, they heavily rely on the sensor type. They even use a total of five different lidar units in their vehicles. The largest scanning lidar on the rooftop, and four non-scanning stage lidars in the rear, in the front and one in each front corner. Waymo has even designed its own lidar sensor for recent models of their vehicles and they even started selling these lidar units to other companies as well but still, with the cost reduced in our sensors, the total lidar cost of one vehicle is likely somewhere around $10,000.

On the other end of the spectrum, is Elon Musk, for example, who strongly opposes the use of lidar in autonomous vehicles based mostly on the observation that human drivers, "they can drive safely," he says, using only their eyes and their brains, which is why autonomous vehicles should also be able to do the same. He even goes as far as saying that everyone using lidar is doomed, that's one of the statements he made in a recent article which appeared on TechCrunch. The question arises whether lidar is really required for self-driving vehicles or not, or are cameras maybe and radar enough to do the job. From a safety viewpoint, the track record of Tesla, for example, is not that great. The last years have seen a number of accidents, even some of them with fatalities, where the autopilot was at least partially involved.

Even though the system is not yet certified for level four or even level five, Tesla drivers should always double-check whether their vehicle is performing correctly. These accidents exposed some gaps in perception, with our current combination of camera and radar. This track record makes me personally believe that another sensor type is needed to double-check the validity of what radar and camera are seeing or not, at least in the first years of autonomous driving. From an engineering viewpoint, it's much easier to generate a reliable reconstruction of a vehicle environment when you have a dense cloud of 3D points available to you, which will significantly speed up the development process in companies all over the globe. The large number of 30 plus companies currently making progress in lidar development, they present us with a perspective of lidar sensors at price points of only a few $100 which are about to hit the market in the years to come.

I believe that the primary driver behind selecting the appropriate sensors will be performance and reliability, and not necessarily cost as the dominant factor. But as of 2020, the time of recording this video, the rates between lidar and radar is still on and will also remain on for the next three to five years at the least. Until then, it makes perfect sense to use lidar sensors for object detection in autonomous vehicles, which is also the primary goal of this lesson here. Welcome to the end of this chapter here. You now know what the different levels of autonomous driving are all about and you have an understanding of the main sensor types that are used in autonomous vehicles.

Also, you are now able to compare sensors such as the camera, the LiDAR sensor, and also the radar to each other and use a set of parameters that's actually used in day to day automotive practice. Now the next chapter will be about getting your feet wet for the first time because you will be writing your first few lines of code in this course. You will be looking at the way more open datasets and you will be extracting actual sensor information from it using the starter code framework we have prepared for you. See you there.

## Additional Content

## LiDAR vs. Radar vs. Cameras
### Sensor Selection Criteria

Selecting an appropriate sensor set for an autonomous vehicle is a delicate task as you need to balance a range of factors from reliability to cost so your company can identify the sweet spot and select the optimal sensor set. As you have learned in the preceding section, there is a discussion going on about which combination of sensors would be necessary to reach full (or even partial) autonomy. In this section, you will learn about sensor selection criteria as well as the differences between camera, LiDAR and radar with respect to each criterion.

In the following, the most typical selection criteria are briefly discussed.

1. **Range** : LiDAR and radar systems can detect objects at distances ranging from a few meters to more than 200m. Many LiDAR systems have difficulties detecting objects at very close distances, whereas radar can detect objects from less than a meter, depending on the system type (either long, mid or short range) . Mono cameras are not able to reliably measure metric distance to object - this is only possible by making some assumptions about the nature of the world (e.g. planar road surface). Stereo cameras on the other hand can measure distance, but only up to a distance of approx. 80m with accuracy deteriorating significantly from there.
1. **Spatial resolution** : LiDAR scans have a spatial resolution in the order of 0.1° due to the short wavelength of the emitted IR laser light . This allows for high-resolution 3D scans and thus characterization of objects in a scene. Radar on the other hand can not resolve small features very well, especially as distances increase. The spatial resolution of camera systems is defined by the optics, by the pixel size on the image and by its signal-to-noise ratio. Details on small object are lost as soon as the light rays emanating from them are spread to several pixels on the image sensor (blurring). Also, when little ambient light exists to illuminate objects, spatial resolution decreases as objects details are superimposed by increasing noise levels of the image sensor.
1. **Robustness in darkness** : Both radar and LiDAR have an excellent robustness in darkness, as they are both active sensors. While daytime performance of LiDAR systems is very good, they have an even better performance at night because there is no ambient sunlight that might interfere with the detection of IR laser reflections. Cameras on the other hand have a very reduced detection capability at night, as they are passive sensors that rely on ambient light. Even though there have been advances in night time performance of image sensors, they have the lowest performance among the three sensor types.
1. **Robustness in rain, snow, fog** : One of the biggest benefits of radar sensors is their performance under adverse weather conditions. They are not significantly affected by snow, heavy rain or any other obstruction in the air such as fog or sand particles. As an optical system, LiDAR and camera are susceptible to adverse weather and its performance usually degrades significantly with increasing levels of adversity.
1. **Classification of objects** : Cameras excel at classifying objects such as vehicles, pedestrians, speed signs and many others. This is one of the prime advantages of camera systems and recent advances in AI emphasize this even stronger. LiDAR scans with their high-density 3D point clouds also allow for a certain level of classification, albeit with less object diversity than cameras. Radar systems do not allow for much object classification.
1. **Perceiving 2D structures** : Camera systems are the only sensor able to interpret two-dimensional information such as speed signs, lane markings or traffic lights, as they are able to measure both color and light intensity. This is the primary advantage of cameras over the other sensor types.
1. **Measure speed** : Radar can directly measure the velocity of objects by exploiting the Doppler frequency shift. This is one of the primary advantages of radar sensors. LiDAR can only approximate speed by using successive distance measurements, which makes it less accurate in this regard. Cameras, even though they are not able to measure distance, can measure time to collision by observing the displacement of objects on the image plane. This property will be used later in this course.
1. **System cost** : Radar systems have been widely used in the automotive industry in recent years with current systems being highly compact and affordable. The same holds for mono cameras, which have a price well below US$100 in most cases. Stereo cameras are more expensive due to the increased hardware cost and the significantly lower number of units in the market. LiDAR has gained popularity over the last years, especially in the automotive industry. Due to technological advances, its cost has dropped from more than US$75,000 to below US$5,000. Many experts predict that the cost of a LiDAR module might drop to less than US$500 over the next few years.
1. **Package size** : Both radar and mono cameras can be integrated very well into vehicles. Stereo cameras are in some cases bulky, which makes it harder to integrate them behind the windshield as they sometimes may restrict the driver's field of vision. LiDAR systems exist in various sizes. The 360° scanning LiDAR is typically mounted on top of the roof and is thus very well visible. The industry shift towards much smaller solid-state LiDAR systems will dramatically shrink the system size of LiDAR sensors in the very near future.
1. **Computational requirements** : LiDAR and radar require little back-end processing. While cameras are a cost-efficient and easily available sensor, they require significant processing to extract useful information from the images, which adds to the overall system cost.

---

## Quizzes

In the following table, the different sensor types are assessed with regard to the criteria discussed above.

Range measurement
Robustness in darkness
Robustness in rain, snow, or fog
Classification of objects
Perceiving 2D Structures
Measure speed / TTC
Package size




Camera
−
−
−
++
++
+
+


Radar
++
++
++
−
−
++
+


Lidar
+
++
+
+
−
+
−

In the quizzes below, you will complete the table from above by adding +, ++ or − in the empty columns.
### Outro
