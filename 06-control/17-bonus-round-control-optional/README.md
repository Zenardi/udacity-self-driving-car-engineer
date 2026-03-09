# Bonus Round: Control [Optional]

> Part of: **PID Control**

## Additional Content

## Additional Resources on Control

Nice work reaching the end of the control content! While you still have the project left to do here, we're also providing some additional resources and recent research on the topic that you can come back to if you have time later on.

Reading research papers is a great way to get exposure to the latest and greatest in the field, as well as expand your learning. However, just like the project ahead, it's often best to *learn by doing* - if you find a paper that really excites you, try to implement it (or even something better) yourself!

Additionally, in the Nanodegree, you can check out the "Extracurriculars" content when outside of a lesson on the left side of the classroom, where there is additional content around one of the topics discussed below, Model Predictive Control (MPC).
##### Optional Reading

All of these are completely optional reading - you could spend hours reading through the entirety of these! We suggest moving onto the project first so you have what you’ve learned fresh on your mind, before coming back to check these out. 

We've categorized these papers to hopefully help you narrow down which ones might be of interest, as well as including their *Abstract* section, which summarizes the paper.

---
### Model Predictive Control (MPC)

[Vision-Based High Speed Driving with a Deep Dynamic Observer](https://arxiv.org/abs/1812.02071) by P. Drews, et. al.
> **Abstract:** In this paper we present a framework for combining deep learning-based road detection, particle filters, and Model Predictive Control (MPC) to drive aggressively using only a monocular camera, IMU, and wheel speed sensors. This framework uses deep convolutional neural networks combined with LSTMs to learn a local cost map representation of the track in front of the vehicle. A particle filter uses this dynamic observation model to localize in a schematic map, and MPC is used to drive aggressively using this particle filter based state estimate. We show extensive real world testing results, and demonstrate reliable operation of the vehicle at the friction limits on a complex dirt track. We reach speeds above 27 mph (12 m/s) on a dirt track with a 105 foot (32m) long straight using our 1:5 scale test vehicle. [...]

---
### Reinforcement Learning-based

[Reinforcement Learning and Deep Learning based Lateral Control for Autonomous Driving](https://arxiv.org/abs/1810.12778) by D. Li, et. al.
> **Abstract:** This paper investigates the vision-based autonomous driving with deep learning and reinforcement learning methods. Different from the end-to-end learning method, our method breaks the vision-based lateral control system down into a perception module and a control module. The perception module which is based on a multi-task learning neural network first takes a driver-view image as its input and predicts the track features. The control module which is based on reinforcement learning then makes a control decision based on these features. In order to improve the data efficiency, we propose visual TORCS (VTORCS), a deep reinforcement learning environment which is based on the open racing car simulator (TORCS). By means of the provided functions, one can train an agent with the input of an image or various physical sensor measurement, or evaluate the perception algorithm on this simulator. The trained reinforcement learning controller outperforms the linear quadratic regulator (LQR) controller and model predictive control (MPC) controller on different tracks. The experiments demonstrate that the perception module shows promising performance and the controller is capable of controlling the vehicle drive well along the track center with visual input.

---
### Behavioral Cloning
The below paper shows one of the techniques Waymo has researched using imitation learning (aka behavioral cloning) to drive a car.

[ChauffeurNet: Learning to Drive by Imitating the Best and Synthesizing the Worst](https://arxiv.org/abs/1812.03079) by M. Bansal, A. Krizhevsky and A. Ogale
> **Abstract:** Our goal is to train a policy for autonomous driving via imitation learning that is robust enough to drive a real vehicle. We find that standard behavior cloning is insufficient for handling complex driving scenarios, even when we leverage a perception system for preprocessing the input and a controller for executing the output on the car: 30 million examples are still not enough. We propose exposing the learner to synthesized data in the form of perturbations to the expert's driving, which creates interesting situations such as collisions and/or going off the road. Rather than purely imitating all data, we augment the imitation loss with additional losses that penalize undesirable events and encourage progress -- the perturbations then provide an important signal for these losses and lead to robustness of the learned model. We show that the ChauffeurNet model can handle complex situations in simulation, and present ablation experiments that emphasize the importance of each of our proposed changes and show that the model is responding to the appropriate causal factors. Finally, we demonstrate the model driving a car in the real world.
