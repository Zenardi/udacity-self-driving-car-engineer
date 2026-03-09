# Waymo: Pose and Frame of Reference

> Part of: **Creating Scan Matching Algorithms**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=HrWmhJM0li0)

## Summary

**Pose Representation**
=======================

This lesson introduces the concept of **pose**, a concise descriptor of an object's position and orientation in 3D space.

### Key Concepts

* **Degrees of Freedom (DOF)**: A measure of the number of independent parameters required to describe an object's position or orientation. For rigid objects, pose is typically described by six DOF: three for position and three for orientation.
* **Rigid Pose**: A representation of an object's position and orientation in 3D space, assuming no deformation or change in shape.
* **Articulated Objects**: Non-rigid objects with multiple joints or parts that can move relative to each other, requiring a higher-dimensional representation of pose (e.g., people, semi-trucks).
* **Frame of Reference**: A reference point or environment used for measurements or observations, which can be an object or the surrounding space.

### Practical Notes

No specific code patterns or real-world applications are discussed in this lesson. However, understanding the concepts of pose and degrees of freedom is crucial for developing algorithms that work with 3D objects, such as computer vision, robotics, and simulation software.

## Transcript

Pose is a concise descriptor of an object position and orientation. Typically for rigid pose, you have its position in the 3D world which is described by three degrees of freedom, and its orientation in space, which is also three degrees of freedom. For example, they can be pitch, roll, and yaw. For objects that are not rigid, in other terms, articulated objects such as people or semi-trucks, you may need a higher dimensional representation of pose than just these six values. A frame of reference consists of an object or an environment relative to which you perform measurements or observations.

## Additional Content

## Waymo: Pose and Frame of Reference

Let's check in with Dragomir at Waymo on quick primers on what "pose" and "frame of reference" are.

### Pose
### Frame of Reference
