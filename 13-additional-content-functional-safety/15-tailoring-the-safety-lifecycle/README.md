# Tailoring the Safety Lifecycle

> Part of: **Functional Safety: Safety Plan**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Ym9raP5zb2U)

## Summary

**V-Model for Functional Safety**
=====================================

The V-model is a framework for managing functional safety throughout the entire product development cycle. It encompasses all aspects of safety, from concept to production.

### Key Concepts
* **Functional Safety Manager**: responsible for coordinating and documenting the entire safety lifecycle.
* **Safety Lifecycle**: consists of the following phases:
	+ Concept phase: defining the product's functionality and requirements
	+ Product development phase: designing and implementing the product
	+ Production phase: manufacturing and testing the final product
* **Tailoring the Safety Lifecycle**: adapting the V-model to only include the parts impacted by new or modified functionality.
* **V-Model Diagram**: a visual representation of the safety lifecycle, showing the relationship between each phase.

### Practical Notes

When modifying an existing product, you may not need to implement all steps in the safety lifecycle. Instead, focus on the parts of the product that are new or have changed. For example:

```markdown
**Example: Updating an Automatic Braking System**

* Determine if the new electronic control unit (ECU) affects the braking system's functionality.
* If not, reuse part of the original functional safety analysis and run tests to ensure integration with the rest of the system.
```

In the safety plan, discuss whether the product is new or a modification, and tailor the safety lifecycle accordingly. This allows you to focus on the parts of the product that are new or have changed.

## Transcript

<v English>Let's look again at the steps contained in the V-model.</v> <v English>The V-model shows the entire safety life cycle,</v> <v English>starting from the concept phase through</v> <v English>their product development and ending in production.</v> <v English>In general, a functional safety manager will</v> <v English>need to coordinate and document the entire cycle.</v> <v English>Ask yourself, is my product new or am I modifying an existing product?</v> <v English>If you are designing a new product,</v> <v English>you'll have to follow and document the entire safety lifecycle.</v> <v English>If you are modifying a product that already exist,</v> <v English>you might not have to implement all of the steps in the safety lifecycle.</v> <v English>New functionality perhaps only impacts</v> <v English>certain parts of the concept phase or product development phase,</v> <v English>so you can tailor the safety lifecycle to include</v> <v English>only the parts impacted by the new functionality.</v> <v English>That way, you can reuse some of the work that has already been done.</v> <v English>Let's say, for example,</v> <v English>that you are working on updating an automatic braking system that already exists.</v> <v English>Your company has decided to use</v> <v English>a new electronic control unit with a faster, more powerful processor.</v> <v English>However, the break system's functionality has not changed.</v> <v English>Your first step is to make sure the new ECU really would not affect the braking system.</v> <v English>If the new ECU has no effect,</v> <v English>you might not have to change anything in the design.</v> <v English>You could also reuse part of the original functional safety analysis.</v> <v English>However, you would still need to run tests to make sure</v> <v English>the new electronic control unit integrates with the rest of the system.</v> <v English>In the safety plan,</v> <v English>you would need to discuss if the product being developed is new or just a modification.</v> <v English>Then you tailor the safety lifecycle and</v> <v English>discuss what sections of the V-model need to be included.</v> <v English>Tailoring the safety lifecycle allows you</v> <v English>to focus on the parts of the product that are new.</v>

## Additional Content

### Tailoring the Safety Lifecycle
### Quiz Safety Culture

Remember safety culture from the last lesson page? Here is a (somewhat tricky) quiz to test what you learned.
