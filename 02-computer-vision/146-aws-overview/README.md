# AWS Overview

> Part of: **Object Detection in an Urban Environment**

## Additional Content

We would use **Amazon Web Services (AWS)** for this project. Here is a brief overview of AWS and some AWS Services that would be used in this project.
### Amazon Web Services (AWS)

Amazon Web Services (AWS) is a collection of digital infrastructure services that developers can leverage when developing their applications. These services are offered by Amazon.com and are hosted on the same infrastructure that Amazon uses to run its own websites.

AWS offers a wide range of services, including storage, compute, and content delivery, as well as many other services such as database, analytics, machine learning, and security. These services are designed to be highly scalable and reliable, and they are delivered over the internet in a pay-as-you-go pricing model.

AWS is widely used because of its flexibility, scalability, and reliability. Developers can use AWS to build a wide range of applications, from simple websites to complex cloud-based applications.
### AWS Services used in the project

1. **Sagemaker**

	Amazon SageMaker is a fully-managed platform that enables developers and data scientists to build, train, and deploy machine learning models quickly. SageMaker simplifies the process of working with machine learning by providing a range of pre-built models and algorithms that can be used out-of-the-box, as well as tools for building, training, and deploying custom models.

	With SageMaker, data scientists and developers can leverage a range of tools and technologies, including Jupyter notebooks, to build and test machine learning models, and then deploy them into a production environment with just a few clicks. SageMaker also provides integration with other AWS services, such as Amazon S3 for storing data and Amazon EC2 for scalable compute resources, making it easy to build and deploy machine learning solutions at scale.

	SageMaker is designed to be easy to use and highly flexible, and it is a popular choice for developers and data scientists who want to build and deploy machine learning models quickly and easily.
    
	>*Note: We would use Sagemaker for running jupyter notebooks, training and deploying the model, and for inference.*

    
2. **Elastic Container Registry**

	Amazon Elastic Container Registry (ECR) is a fully-managed Docker container registry that makes it easy to store, manage, and deploy Docker container images. ECR is a regional service, meaning that the images you store in an ECR registry are stored within an AWS Region, and you can store and manage images in different regions to meet the needs of your applications.

	ECR is integrated with other AWS services, such as Amazon ECS and Amazon EKS, which makes it easy to use ECR as the container image repository for your containerized applications. ECR also integrates with the Docker command-line interface (CLI), so you can use the same Docker commands you are already familiar with to push, pull, and manage images in ECR.

	ECR is highly available and scalable, and it is designed to be secure, with support for resource-based permissions and fine-grained access control. ECR is a popular choice for developers who want to store and manage Docker container images in the cloud.
    
	>*Note: We would use ECR to build the Docker image and create container required for running this project.*


3. **Simple Storage Service**

	Amazon Simple Storage Service (S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. This makes it a great storage solution for a wide range of use cases, such as storing backups, hosting websites, and storing data for analytics and machine learning applications.

	With S3, you can store and retrieve any amount of data, at any time, from anywhere on the web. S3 is designed to provide 99.999999999% durability, and it stores data across multiple devices in multiple facilities to protect against data loss. S3 is also highly available, with read-after-write consistency for PUTS of new objects and eventual consistency for overwrite PUTS and DELETES.

	S3 is a simple and cost-effective storage solution, with a pay-as-you-go pricing model and no upfront costs. It is easy to use, with a simple API and web-based management console, and it integrates with a wide range of applications and services.
    
	>*Note: We would use S3 to save logs for creating visualizations. Also, the data for this project is stored in a public S3 bucket.*
>***Note*** - *You don't need prior AWS expertise for this project. We have handled all the AWS specific overhead in the skeleton code.*
