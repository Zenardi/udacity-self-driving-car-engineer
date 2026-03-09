# Tools, Environment & Dependencies

> Part of: **Introduction to Deep Learning for Computer Vision**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=V35yk4JKfKc)

## Summary

**Getting Started with Course Tools and Data Sets**
=====================================================

This lesson covers the essential tools and data sets required for the course, including Google Cloud Platform (GCP), GitHub, Jupyter Notebooks, and Integrated Development Environments (IDEs).

### Key Concepts
* **Google Cloud Platform (GCP)**: A cloud-based platform used to store and manipulate objects.
* **gsutil**: The command-line interface provided by GCP for managing data stored in the Cloud.
* **GitHub**: A software development and version control platform where code for exercises and projects will be stored.
* **Git commands**: Essential knowledge required for any software engineer, including basic Git operations.
* **Jupyter Notebooks**: A web-based interface for writing and sharing Python code, ideal for rapid prototyping.
* **Integrated Development Environments (IDEs)**: Software applications used to write, compile, and debug code, such as Visual Studio and PyCharm.

### Practical Notes
To get started with the course, you will need to:

1. Create an account on Google Cloud Platform (GCP) to access gsutil.
2. Register directly on the Waymo open data set website to access the camera sensor data.
3. Familiarize yourself with basic Git commands and version control principles.
4. Choose your preferred Integrated Development Environment (IDE), such as Visual Studio or PyCharm.

Note: It may take a day or two to be granted access to the Waymo data set, so it's recommended to register now to avoid any delays.

## Transcript

Let's take some time to talk about the tools you will need during this course. We're going to use a data set that is being hosted on the Google Cloud Platform or GCP. You will need to create an account to be able to use gsutil, the Google command-line interface to manipulate objects stored in the Cloud. Code for the exercises and the project will be stored on GitHub, a software development and version control platform. A good understanding of Git commands is a requirement for any software engineer.

You will also be using Jupyter Notebooks, a web interface to write and share code in Python. Jupyter Notebooks are great for rapid prototyping, and I'm personally a big fan of them. Finally, you will actually write most of the code for exercises in an Integrated Development Environment or IDE. You can use your favorite IDE, but I will personally recommend Visual Studio and PyCharm. Over the course of this nanodegree, we'll be using the Waymo open data sets.

Waymo is one of the leading self-driving car companies in the Silicon Valley, and they built a very unique data set consisting of hundreds of trips made by their self-driving cars consisting of a collection of high-resolution sensor data in diverse environment. In this course, we'll be focusing on the camera sensor. While in other courses in this nanodegree, the Lidar data will be introduced. We'll get to learn more about this data set in later lessons. As of now, you only need to know that a trip is made of a sequence of frames from multiple cameras.

Each single frame is annotated with labels. Your first task is to register directly on the Waymo open data set website, such that you can access the data when you need it. It usually takes a day or two to be granted access to the data set, and I would recommend that you take care of this now. The Waymo data set is unique, and it will give you a good understanding of the kind of data self-driving car engineer deal with. I could not think of any better data set for this nanodegree.

## Additional Content

## Tools, Environment & Dependencies
In this course, you will need the following:
- **Install gsutil:** a Python application to manipulate Google Cloud Storage items. You will find the tutorial to install it [here](https://cloud.google.com/storage/docs/gsutil).
- **Create a Github account:** a version control system. You will need to create an account [here](https://github.com/). You will need a github account to access some of the material and create your submission for the final project. If you already have an account, you are good to go for this step!
- **Set up an Integrated development environment (IDE):** a software application to write code. For this course, I would recommend either [Pycharm](https://www.jetbrains.com/pycharm/) or [VS Code](https://code.visualstudio.com/).
