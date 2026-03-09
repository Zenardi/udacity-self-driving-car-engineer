# Verification and Validation Acceptance Criteria

> Part of: **Functional Safety: Functional Safety Concept**

## Additional Content

### Verification and Validation 

At some point, you need to prove that your safety requirements are actually being met. You would do this on the right side of the V model during validation, verification and testing. 

But in the functional safety concept, you can specify the criteria and methods that will be used later for verification, validation and testing of your functional safety requirements.

For example, we have set a limit on the maximum amplitude allowed in the lane departure warning functionality.

For whatever value we end up choosing for the max torque amplitude, we need to **validate** that we chose a reasonable value. We would need to test how drivers react to different torque amplitudes and frequencies to prove that we chose an appropriate value.

Once we have validated our choice, we then need to **verify** that the safety requirement is met; when the torque amplitude crosses the limit, the lane assistance output is set to zero within the 50 ms fault tolerant time interval. For this specific case, we would probably do a software test inserting a fault into the system and seeing what happens.

For the lane keeping assistance function, we would have to test and validate that the max_duration chosen really did dissuade drivers from taking their hands off the wheel. Then we would verify that the system really does turn off if the lane keeping assistance every exceeded max_duration.
