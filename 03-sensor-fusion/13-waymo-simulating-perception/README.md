# Waymo: Simulating Perception

> Part of: **Introduction to Sensor Fusion and Perception**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=sRy9vYQ6v1c)

## Summary

**Simulation in Perception**
==========================

Perception tasks can benefit greatly from simulation when collecting real data is challenging or impractical. This lesson discusses the advantages of using simulation over real-world data collection, particularly in scenarios where annotating data is difficult or expensive.

### Key Concepts

* **Real vs. Simulated Data**: Real data is often preferred, but simulation can be a cost-effective alternative when collecting and annotating data is challenging.
* **Transfer from Simulation to Reality**: The accuracy of simulated models depends on their ability to transfer well to real-world scenarios, which can be difficult to achieve.
* **Simulation Realism**: Increasing the realism of simulations broadens their applications, but also increases the complexity of achieving accurate transfer to reality.

### Practical Notes

When deciding whether simulation is a suitable tool for your perception task, consider the following:

* If collecting and annotating real data is expensive or impractical, simulation may be a more cost-effective option.
* Be aware that simulations must be carefully designed to accurately represent real-world scenarios in order to achieve good transfer performance.

Example code or formulas are not provided in this lesson. However, understanding the trade-offs between simulated and real-world data collection can help you make informed decisions about which approach is best for your specific project.

## Transcript

Simulation can be quite helpful for perception, especially in the cases when real data is hard to collect. Typically, the best thing you can do if you need more data is to send a vehicle or your sensor setup into the real world and collect many examples of this data. Nothing beats real data in that sense. Except if either the data or the annotations cannot be easily collected. Sometimes it is really, really expensive to do this type of collection or annotating it.

For example, if you want to detect objects really accurately in cameras at very large distance. Maybe you can annotate the object, but it's very hard to annotate their depth. Maybe traditional active sensors don't even reach that far, and this is a case where simulation can be really helpful. Either case, this is very rare objects. For example, constructions on highways with truck sensors, or potentially yellow traffic lights against the sunset, or any interesting scenarios like this.

When simulation becomes more cost-effective than the real data collection, it has a lot to contribute. Now there is a problem with simulation, and again, one that can be solved with up front. The more realistic the simulation is, the broader its applications become. This is work that is happening in our community, the simulators become more and more realistic. But generally, there is the problem of transfer from simulated to real scenarios, and this transfer is sometimes difficult and does not work so well.

So one need to carefully consider for every possible application where the simulation really is the right tool for you.

## Additional Content

## Waymo: Simulating Perception

Simulation is a powerful tool used throughout the autonomous technology stack. Here, Dragomir will discuss its use in aiding perception technologies.
