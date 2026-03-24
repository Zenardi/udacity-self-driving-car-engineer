# Environment Classification

> Part of: **Trajectory Generation**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=4NOvHff7WFQ)

## Summary

**Hybrid A* Algorithm for Trajectory Planning in Unstructured Environments**
====================================================================================

This project explores the use of Hybrid A\* algorithm for finding trajectories in complex, unstructured environments such as parking lots or mazes. Unlike structured environments like highways or streets, these areas have fewer rules and lower driving speeds.

**Key Concepts**
---------------

* **Unstructured Environments**: Areas with few specific rules and changing conditions, such as parking lots or mazes.
* **Structured Environments**: Areas with predefined rules and constraints, such as highways or streets (e.g., direction of traffic, lane boundaries, speed limits).
* **Hybrid A\***: An algorithm that combines the strengths of style-based algorithms (finding solutions everywhere) with the advantages of structured environments (using reference paths and constraints to guide trajectory planning).

**Practical Notes**
------------------

While this lesson does not provide specific code or implementation details for the Hybrid A\* algorithm, it highlights the importance of considering both unstructured and structured environment characteristics when designing autonomous vehicle navigation systems. In practical applications, developers may need to adapt and combine different algorithms to suit the specific requirements of various environments.

Note: This summary is based on a partial transcript, as the provided text appears to be incomplete. If you have access to the full transcript or additional context, please let me know so I can provide a more comprehensive summary.

## Transcript

Correct, you've just implemented Hybrid A* which is one of the best algorithm for finding trajectories in unstructured environments. An example of such an environment is a parking lot or a maze. And these environments tend to have less specific rules than highway or streets and also, lower driving speeds. They also do not have an obvious reference path that corresponds to what we should be driving 90% of the time, because they change so much. On the other hand, highway or streets are very structured environments and in these environments, all motion is more constrained by predefined rules, regarding how we can move on the road. For example, the direction of traffic or lane boundaries or also speed limits. All these rules impose constraints which have to be satisfied but also for guidance regarding what the trajectory should look like. And while a style is great at finding solutions everywhere, it does not take advantage of this information. For example, the road structure itself can be used as a reference path. Let's see how we can u-