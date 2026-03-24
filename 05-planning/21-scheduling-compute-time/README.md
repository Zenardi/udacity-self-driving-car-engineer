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

In the very beginning of the lesson you have already seen this diagram. By now you might be able to guess why the Behavior Module updates on a lower frequency than for example the Trajectory Module. This is due to the fact that the high level decisions made in the behavior module spend a longer time horizon and just don't change as frequently. But the Trajectory Module does still count on our decisions and it's important that the over all system architecture doesn't allow for a comparatively slow module like the behavior planner to clock up the proper functioning of the other faster components. Let's take a second to talk about what's known as a scheduling problem and how it can be handled in the self-driving car. This diagram shows what happens during two processing cycles of the Behavior Module. As you can see, the Prediction Module updates with a higher frequency than Behavior. Trajectory is even higher. And so on. But focus your attention on what happens after behavior has completed its first cycle. To begin its second cycle, the behavior module needs data from prediction and localization. For localization, it's easy in theory since at this instant it will have some fresh data and behavior could just use that. But what about for prediction. It's actually right in the middle of an update cycle at this instant. Should behavior just wait until prediction is done? No. If we start waiting then we block up the pipeline for downstream components. The answer is to use data from here and accept that it's a little stale. When you implement your half planner for the final project, we will provide you with the code that handles all of this. But it's worth mentioning that this is how it's done.