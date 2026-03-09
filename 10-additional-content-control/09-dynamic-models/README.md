# Dynamic Models

> Part of: **Vehicle Models**

## Additional Content

## What we have learned so far
From the previous lessons we have learned to apply the bicycle model, polynomial fitting, low complexity heuristics (e.g. CTE), and short time steps, to enable vehicles to follow a complex (polynomial) trajectories.  This is an effective, practical, and commonly used approach, which can be applied to many autonomous vehicle scenarios, in real time. 

## Coming Next
For the next few lessons we will round out our discussion of vehicle models with an overview of the more comprehensive, but less practical, dynamic models.  Dynamic models and the elements which comprise them are rigorous and could be modules or courses unto themselves.  The content that follows is targeted developing awareness and intuition that can be applied to further study and consists of:

- Dynamic Model Forces
- Tire Slip Angle
- Tire Slip Ratio
- Tire Models

Additional resources are linked to each lesson to encourage and enable more in depth study.  [One of these resources](http://www.me.berkeley.edu/~frborrel/pdfpub/IV_KinematicMPC_jason.pdf)  makes a good case for the use of lower complexity kinematic models, as:

> Compared to higher fidelity vehicle models, the system identification on the kinematic bicycle model is easier because there are only two parameters to identify, lf and lr. This makes it simpler to port the same controller or path planner to other vehicles with differently sized wheelbases.

To further expand on this, lower complexity models have two strong advantages over higher complexity (dynamic included) models.  They can run in real time (essential requirement of any model operating in a vehicle) and they are transferable to vehicles with differing attributes, such as mass.  To use a dynamic model engineers would have to be able to control the vehicle attributes of the vehicles they are deploying models into (they probably won't have control over this).  High complexity models would need major re-adjustment to account for even small differences.  Lower complexity models do not suffer from this constraint and so can be placed in a wider range of vehicles, with far less additional effort, and unpredictability.

Another frequently asked question is where our model comes from and why it differs from other models seen in the program and from other sources.  

The kinematic model we derive and use here is not quite the same as in the Berkeley paper (linked above), although they are similar.  It is possible to use different models in different parts of your pipeline, depending on what levels of accuracy you need in different places.  It is common to see this in industry.  The principles of model we present can be applied to add parameters into the model to make models fit to purpose.
