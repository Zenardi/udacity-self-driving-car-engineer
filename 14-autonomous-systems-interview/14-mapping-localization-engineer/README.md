# Mapping/Localization Engineer

> Part of: **Autonomous Systems Interview Practice**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=rdVJZg4NJtc)

## Summary

**README File: Satellite Positioning and Localization**

This project explores the process of determining an object's position using satellite signals. The main concepts covered include GPS signal reception, coordinate systems (latitude and longitude), and localization algorithms.

### Key Concepts

* **GPS Signal Reception**: Satellites in geosynchronous orbit broadcast signals that are picked up by a GPS device on Earth.
* **Coordinate Systems**: Latitude and longitude coordinates are used to represent an object's position on the Earth's surface.
* **Localization Algorithms**: Techniques such as particle filters and Kalman filters can be used to improve positioning accuracy by combining GPS data with other sensor information.
* **Particle Filters**: A type of algorithm that uses a set of random particles to estimate the object's location, updating the particles based on new measurements.
* **Kalman Filters**: An algorithm that combines prediction and measurement updates to produce an optimal estimate of the object's state.

### Practical Notes

This project can be applied in various fields such as robotics, autonomous vehicles, and drone navigation. While GPS signals can provide a basic level of positioning accuracy (within a few feet), more accurate results can be achieved by combining GPS data with other sensor information using localization algorithms like particle filters or Kalman filters.

Example code snippets for implementing these concepts are not provided in this transcript, but they may involve:

```python
import numpy as np

# Example particle filter implementation
def particle_filter(measurements):
    # Initialize particles
    particles = np.random.rand(1000, 2)

    # Update particles based on new measurements
    for measurement in measurements:
        particles = update_particles(particles, measurement)

    return particles
```

Note that this is a simplified example and actual implementation details may vary depending on the specific requirements of your project.

## Transcript

Hey, welcome here today Mike. I'm really glad to have you in here for the interview. What I'd really like to get started with is just a question around mapping and localization. Are you ready? Sure. Okay, great. So, my first question for you is to just describe the process behind how satellites determine the position of an object. Sure. So, satellites typically float around in geosynchronous orbit, and when they're in that orbit, the Earth is actually spinning and they're actually broadcasting the signal back down. Then, depending on where you are on Earth, you have some sort of a GPS packing, your GPS picks up the signals from the satellites and then translate that to a coordinate or location system using latitude and longitude. Great. Is that usually something that just takes one satellite or do you need multiple satellites to determine this? So, you can do it with one satellite. The problem with one satellite is the area is usually really large, so you typically want anywhere between three to five satellites on average to actually get a much more accurate position. Interesting.

Do you think that's something you can use for like a robotics application or is that more for autonomous vehicles as well, or is that not accurate enough? I think you can use it to some extent depending on how accurate you need to be. In terms of something like a self-driving car maybe, it's just probably not the best. I think you're only accurate within a couple of feet so typically around plus or minus seven feet or so. In that case, you could actually be predicted to be in the different lane. So, that's actually very dangerous in something like a self-driving car. But if I'm flying a UAV or something like that out in the middle of a field, that might be good enough for the purpose that I'm in. Great. Can you think of any approaches that might be more accurate in a robotics approach? So, I think what you could do is you can actually take some of this GPS signal information and you can actually couple it with some different types of algorithm, some sort of localization algorithm something like a particle filter or maybe a common filter. Have you ever implemented something like a particle filter or common filter? Yeah. So, I've done both actually. What did you have to do in order to implement those or what about them makes them better than just GPS? Yeah. So, one of the things that you do is there's typically two phases. So, there's usually a measurement phase and then there's an update phase. So, with the measurement phase, you're actually gathering the information that you've collected from the satellite and making a prediction as to where you're going to move. Then in your update phase, you're looking at where your new location is in the measurement information. Again, adjusting for an error and then kind of going back and fine tuning, so you're basically making a closed feedback loop. Great. Okay.

I think that covers most of what I had for this question. So, let's go ahead and move on to the next topic. Great. Thanks. All right.
