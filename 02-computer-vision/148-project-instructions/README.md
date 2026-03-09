# Project Instructions

> Part of: **Object Detection in an Urban Environment**

## Additional Content

### Object Detection in an Urban Environment

In this project, you will learn how to train an object detection model using the [Tensorflow Object Detection API](https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/index.html) and [AWS Sagemaker](https://aws.amazon.com/sagemaker/). At the end of this project, you will be able to generate videos such as the one below.
### Steps:

* `1_train_model.ipynb` - This notebook is used to train the model. We are using the **EfficientNet** pretrained model as default. So you should be able to run this notebook without making any changes. This will help in understanding how the skeleton code works. However, there are some more tasks to finish here:
	*  	**TODO 1**: Try at least 2 pretrained models (except **EfficientNet**), and report there accuracies.
    >Note: You would need to edit the `pipeline.config` file according to the pretrained model you choose.
    * **TODO 2**: Write a brief summary of your experiments and suggest the best model for this problem. This should include the accuracies (mAP) values of the models you tried. Also discuss:
    	* How does the validation loss compare to the training loss? 
        * Did you expect such behavior from the losses / metrics?
        * What can you do to further improve the performance of the tested models?
    * *Optional 1*: Try various data augmentation strategies to further improve your accuracy.
    * *Optional 2*: Add Tensorboard graphs in your notebook.
* `2_deploy_model.ipynb`: This notebook is used to deploy the model in AWS and run inference.
	* **TODO 3**: Update the model artificats path in this notebook and generate the video output.
>**Important Note** - Stop and delete all the AWS resources once you have finished the project. Ensure that you download the project files locally for backup.
