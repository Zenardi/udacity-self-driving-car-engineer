# Sebastian and Temporal Interference

> Part of: **Functional Safety at the Software and Hardware Levels**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=AD47B4rAKyY)

## Summary

**Summary of Self-Driving Car Challenges**

This lesson discusses the challenges faced by early self-driving cars, specifically the **Stanley** machine that participated in the Darpa Grand Challenge. The machine's ability to detect obstacles was affected by a rare issue where it would occasionally see a "magic big obstacle" and react erratically.

**Key Concepts**

* **Laser scanning**: using laser data to map the terrain
* **Data overlap**: comparing laser data from different time points to ensure accuracy
* **Confidence calculation**: determining confidence levels based on the number of successful laser readings over time
* **Clock synchronization**: ensuring that multiple computers have synchronized clocks for accurate calculations

**Practical Notes**

The lesson highlights the importance of considering seemingly unrelated factors, such as clock synchronization and data overlap, when developing self-driving car systems. The instructor shares a real-world example where a backwards-going clock caused catastrophic effects on the confidence calculation, leading to a rare but critical issue with obstacle detection. This serves as an illustration of the need for thorough testing and attention to detail in software development.

## Transcript

<v English>Early days self-driving car we build a machine to drive through the desert,</v> <v English>Stanley, for the Dawawine Challenge and the machine drove really nicely.</v> <v English>Except every 40 miles or so,</v> <v English>it would see a magic big obstacle in front of</v> <v English>it and freak out and attempt to jump down a cliff.</v> <v English>It was very rare.</v> <v English>It was every 40 miles. It was like every two or three hours.</v> <v English>It was very hard to catch and we were flabbergasted like why all of a sudden,</v> <v English>everything's going perfect, all of a sudden,</v> <v English>dust of all would see this random massive obstacle.</v> <v English>It took me months of my own time to figure that out and fast forward, here is the answer.</v> <v English>We had a laser scanning the terrain and to make</v> <v English>sure that when laser data overlapped over time,</v> <v English>that you could bounce up and down,</v> <v English>that we wouldn't fall into a trap to compare laser data,</v> <v English>that wasn't in the same cone of frame.</v> <v English>We just said look, the less laser reading and some time elapsed.</v> <v English>The more time elapsed, the less confident we are.</v> <v English>It was actually a good rule so we could actually have</v> <v English>a situation if data was acquired very successfully in time, very confident.</v> <v English>We're telling between, we compared all data points, less confidence.</v> <v English>Then, we imported this architecture to multiple computers and exporting,</v> <v English>we had to sync the clocks of those computers.</v> <v English>In the syncing of clocks of those computers,</v> <v English>time would occasionally go backwards.</v> <v English>What that did to our confidences was catastrophic.</v> <v English>It was, all of a sudden, instead of relaxing confidence over time,</v> <v English>tighten confidences to the level that could never see no obstacle.</v> <v English>It was really a combination of clock being backwards, as far as syncing,</v> <v English>and the car bouncing up and down at</v> <v English>the same time that would cause that catastrophic situation.</v> <v English>Now I, as a software engineer,</v> <v English>I wouldn't have asked the question of these bizarre obstacles,</v> <v English>does the clock go backwards?</v> <v English>It took us forever to even look at the right number to understand</v> <v English>that this backwards-going clock could actually cause the car to crash.</v> <v English>That is one of these examples of a really,</v> <v English>really hard to find bug.</v>

## Additional Content

### Temporal Interference Example

In this video, Sebastian discusses an example of temporal interference when developing Stanley for the DARPA challenge.
