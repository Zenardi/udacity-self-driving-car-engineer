# INTRODUCTION TO DEEP LEARNING FOR COMPUTER VISION

- [INTRODUCTION TO DEEP LEARNING FOR COMPUTER VISION](#introduction-to-deep-learning-for-computer-vision)
- [Prerequisites](#prerequisites)
- [Lesson Outline](#lesson-outline)
  - [Summary](#summary)
- [Course Outline](#course-outline)
  - [Summary](#summary-1)
- [Key Stakeholders](#key-stakeholders)
- [Introduction to Deep Learning and Computer Vision](#introduction-to-deep-learning-and-computer-vision)
  - [Summary](#summary-2)
- [Supervised Learning](#supervised-learning)
  - [Summary](#summary-3)
- [Why CV Is Important for SDC](#why-cv-is-important-for-sdc)
  - [Summary](#summary-4)
- [When to Use Deep Learning for Computer Vision](#when-to-use-deep-learning-for-computer-vision)
  - [Summary](#summary-5)


# Prerequisites

Before we get started,I want to be sure that you have the right background.To get the best possible experience from this course,we're asking you to be proficient in Python.You need to be familiar with the concept of object-oriented programming,as well as the numpy and matplotlib libraries.This entire course will be taught in Python,and I will not go over this concept during the course.Because computer vision and machine learning requires some mathematical background,you will need to have some basic Calculus skills,such as derivative calculations,as well as some basic linear algebra knowledgesuch as matrix multiplication and dot products.Being familiar with those concept is necessary to understand the content of this course,which I'm going to describe in the following videos.

# Lesson Outline
At the beginning of each lesson,I will introduce the content of that lesson.In this introductory lesson,we'll talk about the following, first,we'll start with the course outline,where I will describe the different lessons of this course.Like in self-driving cars systems,deep learning is at the core of this course,and we will spend some time introducing some high-level concept.Then we'll learn about computer vision in the context of self-driving cars.As future self-driving car engineers,you should not only know about the different aspect of the technology,but you should also understand who will be impacted by it.We will review together the different stakeholders of the self-driving car technology.We'll follow with a quick overview of the history of deep learning.Because this course will require you to implement code,we'll review some of the tools you will need.Finally, I will introduce the final project with which the course ends.

In this lesson, we'll look at the following:

* The overall course outline
* An introduction to computer vision in the context of self driving car (SDC)
* Why do we need cameras in SDC?
* Going from classic computer vision to Deep Learning
* The challenges of detecting objects in SDC
* Tools and Environment for the Course
* The Final Course Project

## Summary
The "Lesson Outline" video introduces the key topics that will be covered in the lesson. It begins with an overview of the course structure, highlighting the importance of deep learning in the context of self-driving cars (SDC). The video discusses the role of cameras in SDC and transitions from classic computer vision techniques to deep learning approaches.

It also addresses the challenges of detecting objects in SDC and outlines the tools and environment that will be utilized throughout the course. Finally, the video provides a brief introduction to the final project that students will complete by the end of the course. Overall, it sets the stage for what students can expect to learn and accomplish in the lesson.

# Course Outline
What is this first course about?In this lesson, I'm going to introduceyou the concept of computer vision and deep learning.The goal of this course is to teach you how to become machine learning engineers.Therefore, the second lesson,we'll focus on the machine learning workflow,which will give you an overview of the work of the machine learning engineer.You will learn how to think about the machine learning problem.Any machine learning engineer will tell you the following;being a machine learning engineer,means spending a lot of time with data.Since we are focusing on digital images in this course,we'll spend an entire lesson on the camera sensor.With this knowledge, you will be able tostart building your first machine learning models.We'll get started with linear regression,but rapidly move to the core family of algorithm of this course, neural networks.Using neural networks, and especially using convolutional neural network,we'll learn how to classify images.Finally, we will usethose convolutional neural networks to detect and classify object on images.Throughout this course, you will have exercises andquizzes to practice and deepen these newly acquired skills.This course ends with the final project,where you will solve your first real life machine learning problem.

The overall course is structured as follows:

* Introduction to Deep Learning for Computer Vision (this lesson)
* Overview of the Machine Learning Workflow
* Linear and Logistic Regression: Introduction to Neural Networks
* Classify Images using a Convolutional Neural Network
* Detect Objects in an Image
* Final Project

## Summary
The "Course Outline" video provides an overview of the structure and key components of the course. It begins by introducing the concept of computer vision and deep learning, emphasizing the goal of training students to become machine learning engineers. The video outlines the progression of the course, starting with an overview of the machine learning workflow, followed by lessons on linear regression, neural networks, and convolutional neural networks (CNNs) for image classification.

It also mentions the importance of understanding camera sensors and how they relate to digital images. The course culminates in a final project where students will apply their knowledge to solve a real-world machine learning problem. Throughout the course, students will engage in exercises and quizzes to reinforce their learning. Overall, the video sets clear expectations for what students will learn and achieve by the end of the course.

# Key Stakeholders
Self-driving cars are not only a very exciting technology from an engineering point ofview but it will also dramatically impact our lives when deployed at scale.Because self-driving calls at the highest level ofautonomy will not require any attention from the driver,the commute experience will be improved.Commuters will be able to re-invest the timespent in the car to focus on other activities.With a wide adoption of self-driving cars,we will also observe a reduction oftraffic as well as the reduction of the number of accident.Ultimately, we could imagine cities where self-driving cars have beingused as taxis and people would not necessarily use their own vehicles anymore.The number of parking lots will be reduced and the layoutsof modern cities built around cars will be impacted.This would also limit the number of cars and circulation and diminish the air pollution.Because self-driving cars have such a huge potential impact on society,many stakeholders can be considered,such as insurance companies,city planners, lawmakers, and daily drivers.Many layers of engineering are required to develop self-driving car system andeach team will play a critical role inthe deployment and maintenance of self-driving cars.We'll review some of the engineering teams involved in this process.The data operation team, for example,focuses on the data acquisition by driving prototypes around the city.They also manage the data labeling and the city mapping processes.The hardware team works on improving the different sensors of the self-driving car,such as Lidar or cameras and also developsembedded system to run a different algorithm in the car directly.Because data is at the core of the self-driving car technology,an the entire team is dedicated to data pipelines to ensure thatdata is flowing from the sensor to the Cloud where it's being stored.The research and development team focuses on improving the different algorithmsdeployed in the car from detecting objects to plan optimal trips.Many other teams are also involved,such as ones developing the user-interface.I hope this gives you a good overview ofthe different stakeholders of the self-driving car technologies,from the daily drivers to the different engineering team developing it.Self-driving car will have a huge impact on our lives and Icannot wait to live in a future where this technology is deployed at scale.

Self-driving cars or autonomous vehicles will have a huge impact on our society once the technology is deployed at scale. The following articles highlight the [economic impact](https://www.bosch.com/stories/economic-impact-of-self-driving-cars/#:~:text=Self%2Ddriving%20cars%20will%20change,a%20thing%20of%20the%20past.&text=According%20to%20a%20McKinsey%20study,and%20cities%20from%202030%20onwards.) as well as the [broader consequences](https://www.investopedia.com/articles/investing/052014/how-googles-selfdriving-car-will-change-everything.asp) of the technology.


# Introduction to Deep Learning and Computer Vision
Let's now talk about machine learning.But before we can understand what machine learning is,we need to take a step back and look at a broader concept, Artificial Intelligence.A system is defined as intelligent when it's able to learn fromexternal data and use this knowledge to achieve specific task.You've been interacting with AI for a long time.For example, video games non playable characters,are a type of AI.What differentiate machine learning from such a type ofartificial intelligence is the necessity of being explicitly programmed.Let's consider a game of Tic-Tac-Toe example.Well, you could build an AI using a hard-coded set of rule,such as if my open-end text one corner,text the opposite corner.However, machine learning algorithm do notneed such hard-coded rules and learn from data instead.To do so, we will have to gather data frompreviously played game and train an algorithm to learn from that data.Let's now talk about deep learning,a subset of machine learning algorithm.While deep learning finds it foundation on neural network,a type of machine learning algorithm.The term deep learning illustrates the number of layers in such network.How is deep learning exactly different from machine learning?Well, one great thing about deep learning is the ability to work with raw data.Whereas for machine learning,we sometimes need to handcraft features.Let's consider an example.We are trying to classify an image as containing a dog or not.Well, a machine learning approach will consist in building dog features such as the nose,or ears detectors and find these features in the image.Deep learning, however, we directly takethe image and compute the most meaningful features to classify a dog.It does come at a cost though,which is the amount of data required to train good deep learning algorithms.In this course, we are going to study a couple of machine learning algorithms,such as linear regression and logistic regression.But we will quickly shift to neural network anddeep learning because they are the core of the self-driving car technology.In this course, we're going to focus on a specific class of machine learning problems,which is supervised learning.To use supervised learning,we need labeled data.But what do I mean by that?Well, to train a machine learning algorithm,we need to give the algorithm example of data.But in the case of supervised learning,we also need to annotate or label that data.For example, let's say that you're trying to builda machine learning algorithm that classifies cats and dogs from images.To do so, you gather hundreds of images of both animals.However, before you can use this data in your supervised learning approach,you need to associate a cat or dog label to each image in your data-set.In unsupervised learning, however,we can feed the algorithm directly the raw, unlabeled data.An example of such an algorithm would be a clustering algorithm.Where we try to group data in clusters by using shared features.What are the downsides of supervised learning?Well, the labeling task can come at a great cost.Actually, with the deep learning revolution,some companies solely focus on labeling data for deep learning teams.Where some tasks like classification,where we attribute a single label to an image,do not require lengthy labeling process.Other task, such as object detection,may take much longer because we need to annotate every single object in the image.These schools will be entirely focusing on supervised learning.But fear not, you will have access to labeled data-sets.

* Artificial Intelligence (AI): a system that leverages information from its environment to make decisions. For example, a video game bot.
* Machine Learning (ML): an AI that does not need to be explicitly programmed, and instead learns from data. For example, a spam classification * algorithm.
* Deep Learning (DL): a subset of ML algorithms that do not require handcrafted features and can work with raw data. For example, an object detection algorithm with a convolutional neural network.


## Summary
The "Introduction to Deep Learning and Computer Vision" video provides an overview of the fundamental concepts and significance of deep learning in the field of computer vision. It begins by defining artificial intelligence, machine learning, and deep learning, explaining how deep learning is a subset of machine learning that utilizes neural networks to analyze and interpret visual data.

The video discusses the importance of computer vision in various applications, such as self-driving cars, facial recognition, and image classification. It highlights the advancements in deep learning techniques that have improved the accuracy and efficiency of computer vision tasks. Additionally, the video sets the stage for the course by outlining the key topics that will be covered, including neural networks, convolutional neural networks (CNNs), and practical applications in the real world.

Overall, it aims to inspire students by showcasing the potential of deep learning and computer vision to solve complex problems and drive innovation in technology.

# Supervised Learning
Before we learn more about machine learning,I wanted to introduce some naming convention of supervised learning.Let's consider the task of classifying traffic signs.We're building a supervised learning algorithm to classify a traffic sign image.This image will be the input or input variable to our model.We can also use the letter x to describe it,as well as the term observation.Our algorithm will predict a class using this image.In this case, the class is traffic lights aheadsign depending on whether this class has been predicted or annotated,we'll use different terms.We will use Ŷ or output variable in the case of prediction,for an annotation, we will use the term ground truth,label, or just the letter y.Keep in mind these definitions as those termsare going to frequently come back in later lessons.

In this course, we will focus on supervised learning, where we use annotated data to train an algorithm. In supervised learning, we will define the following:

* Input variable / X / Observation: the input data to the algorithm. For example, in spam classification, it would be an email.
* Ground truth / Y / label: the known associated label with the input data. For example, a human created label describing the email as a spam or not.
* Output variable / Y^ / prediction: the model prediction given the input data. For example, the model predicts the input as being spam.

## Summary
The "Introduction to Deep Learning and Computer Vision" video provides a foundational overview of the concepts and significance of deep learning within the realm of computer vision. It begins by defining key terms such as artificial intelligence (AI), machine learning (ML), and deep learning (DL), explaining how deep learning is a subset of machine learning that utilizes neural networks to process and analyze visual data.

The video highlights the applications of computer vision in various fields, including self-driving cars, facial recognition, and image classification, showcasing the impact of deep learning techniques on improving accuracy and efficiency in these tasks. It sets the stage for the course by outlining the topics that will be covered, such as neural networks, convolutional neural networks (CNNs), and practical applications in real-world scenarios.

Overall, the video aims to inspire students by demonstrating the potential of deep learning and computer vision to solve complex problems and drive technological innovation.


# Why CV Is Important for SDC
To build intelligent cars that are able tonavigate through environments as complex as cities,we need to provide some usable signal.How is our car going to decide when to turn or stop?Well, obviously, it needs some understanding of its environment.The same way that humans are using their eyes to analyze the road when driving,cars are going to use cameras.The field of computer vision consists in a range of techniques that allowa computer to get a high-level understanding of its environment from digital images.For example, let's look at this image of a busy road together.What information do you think is relevant for the self-driving car system?Well, we could start by detecting all the car on image.We can also detect and read traffic signs,such as stop signs,which will be important fora self-driving car system to take into account when making decisions.Finally, we also need to detect pedestrians.All these objects will be taken into account bythe self-driving car system to make optimal decisions.You can now easily understand whycomputer vision is at the core of the self-driving car system.Some self-driving car system also use another type of sensor called Lidar,but this will be covered in another course of this of this nanodegree.

Self-driving cars have multiple sensors, such as cameras, radar or lidar. In this course, we will focus on the **camera sensor**. Using this sensor, the system will be able to perform multiple tasks critical to its autonomy, such as detecting pedestrian, lanes or traffic signs. Later in the Nanodegree, you will perform **sensor fusion** using camera and lidar data!

## Summary
The "Why CV Is Important for SDC" video explains the critical role of computer vision (CV) in self-driving cars (SDC). It begins by highlighting the necessity for autonomous vehicles to understand their environment, similar to how humans use their eyes while driving. The video discusses how CV techniques enable cars to interpret visual data from cameras, allowing them to detect essential elements such as pedestrians, lane markings, and traffic signs.

These detections are crucial for making informed driving decisions, such as when to stop or turn. The video also mentions the integration of other sensors, like Lidar, for enhanced perception, which will be covered later in the course. Overall, it emphasizes that computer vision is at the core of enabling self-driving cars to navigate complex environments safely and effectively.


# When to Use Deep Learning for Computer Vision
Previously, we discovered how computer visionis at the core of the self-driving car technology.Analyzing digital images is critical to createan intelligent car that can navigate complex environments.But to do so, we needperformance algorithm to get the best understanding of an image possible.Well, it appears that Deep Learning is doing very well at image analysisand tend to have much better performances than traditional computer vision method.Moreover, Deep Learning algorithms are able to extractsignals from complex environments such as busy city centers.However, the field of computer vision existed way before the Deep Learning revolution.Whereas Deep Learning excels at certain tasks such as object detection,it should not necessarily be the default algorithm when it comes to analyzing images.For example, Deep Learning comes ata computational cost because of the complexity of the algorithm.Because of said complexity,they are harder to deploy in self-driving carssystem where hardware is often a limitation.Overall, Deep Learning approaches tend to outperformtraditional computer vision method and they are definitely atthe core of many self-driving car systems.However, classic computer vision methods should not beoverlooked and they can be particularly useful in many cases.

Deep Learning algorithms are now the **state of the art (SOTA)** in most computer vision problems, such as image classification or object detection. Therefore, they are now in every SDC system. However, using deep learning adds additional constraints to the system because they require more computational power.

## Summary
The "When to Use Deep Learning for Computer Vision" video discusses the scenarios in which deep learning techniques are most effective for computer vision tasks. It emphasizes that deep learning algorithms have become the state-of-the-art (SOTA) for various computer vision problems, such as image classification and object detection.

The video outlines the advantages of using deep learning, including its ability to handle large datasets and complex patterns that traditional methods may struggle with. However, it also highlights the additional computational resources required for deep learning models. The video provides examples of situations where deep learning is particularly beneficial, such as detecting cars, reading characters on traffic signs, estimating pedestrian poses, and classifying activities from videos.

Overall, the video serves as a guide for understanding when deep learning is the appropriate choice for tackling computer vision challenges.