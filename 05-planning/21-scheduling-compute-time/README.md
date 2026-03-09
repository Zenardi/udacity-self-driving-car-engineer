# Scheduling Compute Time

> Part of: **Behavior Planning**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=N6AlIUczqRM)

## Summary

**Behavior Module Scheduling and Data Management**

The Behavior Module in a self-driving car system updates at a lower frequency than other modules, such as the Trajectory Module. This is because high-level decisions made by the behavior module have a longer time horizon and don't change as frequently.

### Key Concepts

* **Scheduling problem**: A scheduling problem occurs when a slower component (in this case, the Behavior Module) needs data from faster components (Prediction and Localization Modules), but cannot wait for them to complete their update cycles.
* **Pipeline blocking**: If the Behavior Module waits for Prediction to complete its update cycle, it will block the pipeline for downstream components, causing system performance issues.
* **Data staleness**: To avoid pipeline blocking, the Behavior Module can use stale data from Prediction and accept that it may not be up-to-date.

### Practical Notes

When implementing a half planner for your final project, you will need to handle scheduling and data management between modules. The instructor mentions that the code handling this will be provided, but notes that understanding how it works is important for system performance and architecture.

## Transcript

<v English>In the very beginning of the lesson you have already seen this diagram.</v> <v English>By now you might be able to guess why the Behavior Module</v> <v English>updates on a lower frequency than for example the Trajectory Module.</v> <v English>This is due to the fact that the high level decisions made in</v> <v English>the behavior module spend a longer time horizon and just don't change as frequently.</v> <v English>But the Trajectory Module does still count on</v> <v English>our decisions and it's important that the over all system architecture</v> <v English>doesn't allow for a comparatively slow module like</v> <v English>the behavior planner to clock up the proper functioning of the other faster components.</v> <v English>Let's take a second to talk about what's known as</v> <v English>a scheduling problem and how it can be handled in the self-driving car.</v> <v English>This diagram shows what happens during two processing cycles of the Behavior Module.</v> <v English>As you can see, the Prediction Module updates with a higher frequency than Behavior.</v> <v English>Trajectory is even higher. And so on.</v> <v English>But focus your attention on what happens after behavior has completed its first cycle.</v> <v English>To begin its second cycle,</v> <v English>the behavior module needs data from prediction and localization.</v> <v English>For localization, it's easy in theory since at</v> <v English>this instant it will have some fresh data and behavior could just use that.</v> <v English>But what about for prediction.</v> <v English>It's actually right in the middle of an update cycle at this instant.</v> <v English>Should behavior just wait until prediction is done?</v> <v English>No. If we start waiting then we block up the pipeline for downstream components.</v> <v English>The answer is to use data from here and accept that it's a little stale.</v> <v English>When you implement your half planner for the final project,</v> <v English>we will provide you with the code that handles all of this.</v> <v English>But it's worth mentioning that this is how it's done.</v>
