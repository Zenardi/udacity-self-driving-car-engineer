# Training Tips #1

> Part of: **Object Detection in Images**

## Video

[Watch on YouTube](https://www.youtube.com/watch?v=7NdZN1336oE)

## Summary

**Optimizing GPU Usage for Deep Learning**

This project aims to maximize the benefits of using Graphics Processing Units (GPUs) for deep learning tasks by optimizing data transfer processes and leveraging the strengths of both CPUs and GPUs. This README file summarizes key concepts, practical steps, and real-world applications covered in this lesson.

### Key Concepts

* **GPUs vs. CPUs**: Understanding the trade-offs between GPU and CPU performance, including processing speed, bandwidth, and core count.
	+ CPUs are faster but have lower bandwidth, making them suitable for data loading and preprocessing tasks.
	+ GPUs are slower but can process more data at once, making them ideal for heavy computation tasks like matrix operations.
* **Data Transfer Optimization**: The importance of optimizing data transfer between the CPU and GPU to maximize GPU usage.
* **GPU Monitoring Tools**: Using `nvidia-smi` and `nvtop` to monitor GPU performance, memory usage, and temperature in real-time.
	+ `nvidia-smi`: Displays information about driver version, CUDA version, available GPUs, and memory usage.
	+ `nvtop`: Passes information from `nvidia-smi` and displays it in a real-time plot for monitoring GPU utilization and memory usage over time.

### Practical Notes

* **Using `nvidia-smi`**: To monitor GPU performance, use the following command: `nvidia-smi`. This will display useful information about driver version, CUDA version, available GPUs, and memory usage.
* **Monitoring GPU Utilization with `nvtop`**: Use `nvtop` to monitor GPU utilization and memory usage over time. This tool is especially useful for detecting problems in the data pipeline, such as drops in GPU utilization due to slow data loading processes.
* **Optimizing Data Pipelines with TensorFlow Dataset API**: Leverage the TensorFlow Dataset API to create efficient data pipelines by:
	+ Prefetching data while the GPU works on a current batch using the `prefetch` argument.
	+ Parallelizing CPU calls for tasks like data extraction or transformation.
	+ Caching files to avoid reopening them after the first epoch.

By following these key concepts and practical steps, you can optimize your deep learning workflow and maximize the benefits of using GPUs.

## Transcript

As I mentioned previously, training deep neural network takes time and money. It is expensive mostly because it requires graphical processing units or GPUs. GPUs are great for deep learning because they can process a lot of computation in parallel. It will simply not be possible to train some of the deep neural network we have seen in this class on a CPU. However, GPU are expensive, and you want to maximize the benefits you're getting from using them.

To do so, you want to make sure that the data transfer processes in your training code are optimized. Before we see how CPU and GPU interact when training a neural network, let's consider the strengths and weaknesses of both. CPUs run operation very fast. However, they have a lower bandwidth, meaning that they cannot process a lot of data at once. CPUs are made of basic processing units called cores.

For example, modern CPU have 4-8 cores. GPUs are somewhat the opposite. They are a little slower. They can process a lot more data at once. They're also made of thousands of cores.

Let's see how we can leverage these characteristic in a deep learning workflow. Because the CPU is faster, you use for data loading. It will read the files from disk, perform any sort of preprocessing such as image augmentation, and fit the data to the GPU. The GPU is a little slower, but can perform much heavier computation, especially matrices operation. The forward and backward passes will be performed on the GPU where the models weight live.

Let's see what tools we can use to monitor the data transfer between the CPU and the GPU. In this video, we're going to learn about two very useful tools to maximize your GPU usage. For the final project, you'll be using NVIDIA GPUs. NVIDIA is a GPU manufacturer. The GPUs are the most popular when it comes to deep learning application.

The first command line you will be using is nvidia-smi. It contains a lot of useful information. First, you can learn about the driver and CUDA version. I won't get into too much detail here, but it's important to know where you can find this information, as mismatching CUDA version can lead to a lot of headaches. This section here indicate the number of GPU available on your machine, as well as the type of GPU.

On this machine, we have one Tesla K80 GPU. We can also monitor the GPU temperature. Finally, we're mostly going to be interested in using these two section; the memory usage and the GPU utilization. The memory usage indicates how much space is available on the GPU. For example, right now we're using 19 megabytes out of 11 gigabytes.

Once the deep learning model is loaded to the GPU, this number will greatly increase. By using this command, we know if we have space for larger models or larger batch sizes. The GPU utilization displays how much processing the GPU is doing. Because we're not performing any calculations at the moment, it stands at zero percent. Let's see how we can leverage that information to detect any problem with our data pipeline.

If we want to look at the GPU utilization and memory usage over time, we need to use nvtop. Nvtop simply passes information from nvidia-smi and display it in real time. At the top here, we find the same information than nvidia-smi was providing, such as the type of GPU or the temperature. But the real value of nvtop comes from the real-time plot. On this plot, we can monitor the GPU and memory utilization over time.

This is going to be extremely useful to find any problems with our data pipeline. In particular, we're going to look for these patterns where the GPU usage drops significantly. We see a drop of GPU utilization when our data loading processes are slower than GPU processing. In this cases, the system is faster to process forward and backward passes than loading the data, and the GPU is just waiting for more data to process. In the next slide, we'll see how we can fix this.

Finally, it is worth noting that the different processes using the GPU are listed in nvtop. In the next slide, we'll see how the TensorFlow dataset class can help optimizing our data pipelines. The dataset class in TensorFlow can help us create efficient data pipelines. By default, the dataset class waits for the current batch of data to be processed by the GPU before loading the next batch. However, using the prefetch argument, we can preload the data while the GPU is working on a current batch.

Moreover, with the TensorFlow Dataset API, we can parallelize over processes such as data extraction or transformation over the CPU calls to speed the process up. Finally, because we're going to reuse the same files multiple times, we're training a neural network over multiple epochs. The TensorFlow Dataset API allows caching, which avoid reopening the files after the first epoch. The TensorFlow Object Detection library is already relying on this API. We should keep this principle in mind when you create your own training workflows.

## Additional Content

## Training Tips #1
Training a deep learning model requires data transfers from the **CPU** to the **GPU**. Such data transfers can create a bottleneck, slow down your training and cost you a lot of money. Because CPUs and GPUs have different limitations, it is critical to understand where your data is moving from one device to another and how to identify any potential problems with your training pipelines.


**nvtop** is a great, [open source](https://github.com/Syllo/nvtop) tool to track the performances of your GPU. It is the GPU version of [htop](https://htop.dev/) and is very useful to identify any potential issues with your training pipeline. 

A very common problem when training deep neural network is the GPU idling because it is not receiving data fast enough. In other words, the data is processed faster by the GPU than it is being loaded by the CPU.
