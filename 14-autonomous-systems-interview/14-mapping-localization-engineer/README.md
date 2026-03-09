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

<v English>Hey, welcome here today Mike.</v> <v English>I&#39;m really glad to have you in here for the interview.</v> <v English>What I&#39;d really like to get started with is</v> <v English>just a question around mapping and localization. Are you ready?</v> <v English>Sure.</v> <v English>Okay, great. So, my first question for you is to just describe</v> <v English>the process behind how satellites determine the position of an object.</v> <v English>Sure. So, satellites typically float around in geosynchronous orbit,</v> <v English>and when they&#39;re in that orbit,</v> <v English>the Earth is actually spinning and they&#39;re actually broadcasting the signal back down.</v> <v English>Then, depending on where you are on Earth,</v> <v English>you have some sort of a GPS packing,</v> <v English>your GPS picks up the signals from the satellites and then translate</v> <v English>that to a coordinate or location system using latitude and longitude.</v> <v English>Great. Is that usually something</v> <v English>that just takes one satellite or do you need multiple satellites to determine this?</v> <v English>So, you can do it with one satellite.</v> <v English>The problem with one satellite is the area is usually really large,</v> <v English>so you typically want anywhere between three to five satellites</v> <v English>on average to actually get a much more accurate position.</v> <v English>Interesting.

Do you think that&#39;s something you can use for like</v> <v English>a robotics application or is that more for autonomous vehicles as well,</v> <v English>or is that not accurate enough?</v> <v English>I think you can use it to some extent depending on how accurate you need to be.</v> <v English>In terms of something like a self-driving car maybe,</v> <v English>it&#39;s just probably not the best.</v> <v English>I think you&#39;re only accurate within</v> <v English>a couple of feet so typically around plus or minus seven feet or so.</v> <v English>In that case, you could actually be predicted to be in the different lane.</v> <v English>So, that&#39;s actually very dangerous in something like a self-driving car.</v> <v English>But if I&#39;m flying a UAV or something like that out in the middle of a field,</v> <v English>that might be good enough for the purpose that I&#39;m in.</v> <v English>Great. Can you think of any approaches that</v> <v English>might be more accurate in a robotics approach?</v> <v English>So, I think what you could do is you can actually take some of</v> <v English>this GPS signal information and you can</v> <v English>actually couple it with some different types of algorithm,</v> <v English>some sort of localization algorithm something</v> <v English>like a particle filter or maybe a common filter.</v> <v English>Have you ever implemented something like a particle filter or common filter?</v> <v English>Yeah. So, I&#39;ve done both actually.</v> <v English>What did you have to do in order to implement those or</v> <v English>what about them makes them better than just GPS?</v> <v English>Yeah. So, one of the things that you do is there&#39;s typically two phases.</v> <v English>So, there&#39;s usually a measurement phase and then there&#39;s an update phase.</v> <v English>So, with the measurement phase, you&#39;re actually gathering the information that</v> <v English>you&#39;ve collected from the satellite</v> <v English>and making a prediction as to where you&#39;re going to move.</v> <v English>Then in your update phase,</v> <v English>you&#39;re looking at where your new location is in the measurement information.</v> <v English>Again, adjusting for an error and then kind of going back and fine tuning,</v> <v English>so you&#39;re basically making a closed feedback loop.</v> <v English>Great. Okay.

I think that covers most of what I had for this question.</v> <v English>So, let&#39;s go ahead and move on to the next topic.</v> <v English>Great. Thanks.</v> <v English>All right.</v>
