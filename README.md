Vulkan Flocking: compute and shading in one pipeline!
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Richard Lee
* Tested on: Windows 7, i7-3720QM @ 2.60GHz 8GB, GT 650M 4GB (Personal Computer)

<img src="img/flocking.gif" width="800">

* Why do you think Vulkan expects explicit descriptors for things like
generating pipelines and commands?

This is likely due to the fact that Vulkan does not manage the pipeline for the developer, and interfaces with the GPU at a low level. This means that the developer must provide explicit descriptors to specify how the pipeline and commands should be executed. In addition, since Vulkan uses "pools" of memory for command buffers and descriptor sets to avoid having to manage memory, the descriptors must manually manage the memory throughout the pipeline.

* Describe a situation besides flip-flop buffers in which you may need multiple
descriptor sets to fit one descriptor layout.

Since descriptor sets simply specify the input arguments to a specific input format, another situation using multiple descriptor sets could just be passing in two different sets of data to a single shader, such as passing in two separate input models into a vertex shader.

* What are some problems to keep in mind when using multiple Vulkan queues?

Since different queues may be backed by different hardware, certain commands may work on one set of hardware but not another, so it is important to keep hardware compatibility in mind. In addition, since the same buffer can be used across multiple queues, write conflicts and race conditions should be avoided through the use of fences to allow synchronization.

* What is one advantage of using compute commands that can share data with a
rendering pipeline?

Data does not need to be transferred from the compute to the rendering stage on each call, which makes sharing data far less expensive.

### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)
