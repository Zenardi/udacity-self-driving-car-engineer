# Interlude: Using The AMI

> Part of: **Inference Performance**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=Y2ggt6l7PTo)

## Additional Content

Running many of the optimizations in TensorFlow requires compiling the TensorFlow and its associated tools from source. This process can be tedious so we've created an AMI, `	
udacity-carnd-advanced-deep-learning` available in the N. California, Oregon, N. Virginia, and Ohio regions.

For this guide we'll be creating a spot instance since they are easier to setup and generally much cheaper than regular instances. The downside of a spot instance is it may be terminated at any point. Creating a persistent volume and saving the model frequently is a good strategy.

## GPU Instance and AMI

The first thing we'll do is select the AMI and an instance with a GPU:


## Volume, Key Pair, and Security Group

**NOTE**: during the project you should uncheck the volume delete marker, this will ensure the volume is **NOT** deleted when the instance is terminated and your progress will be saved. The volume can then be attached to a future instance.
## Connecting To The Instance


Please note that in some cases, the default security group blocks SSH connections from external IPs, resulting in the request timing out. In these cases, the security group has to be updated to allow SSH connections.  Please see [this post](https://knowledge.udacity.com/questions/6725) for details as well as these helpful setup instructions: 

*Adapted from mentor driveWell's advice*:

1. Log in to EC2 management console, region [N. California, Oregon, N. Virginia, or Ohio]
2. Instances -> spot requests -> Request Spot Instances
3. Search for AMI -> Communiti AMI -> udacity-carnd-advanced-deep-learning
4. Instances type(s) select -> g2.2xlarge or g3.4xlarge is suggested (GPU instances)
5. Network default -> Next
6. EBS volumes -> Delete: uncheck mark (important: storing the data when instance is terminated will be charged additionally)
7. Key pair name -> create new key pair -> update -> choose
8. Security group -> create new -> add SSH and custom TCP for port 8888
9. Review -> Launch
10. Instances -> when Instance State = Running -> right click -> Connect
11. If using Putty (Windows), follow instructions for Putty from here
