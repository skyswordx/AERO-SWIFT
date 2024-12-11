# 复刻 Elastic Tracker 时的一些问题

项目地址：[ZJU-FAST-Lab/Elastic-Tracker: Elastic Tracker: A Spatio-temporal Trajectory Planner Flexible Aerial Tracking](https://github.com/ZJU-FAST-Lab/Elastic-Tracker)

## 1. 显卡架构、cuda-tooklit 和 nvcc 编译选项


这个项目如果不配置好 cuda 的话，在 catkin_make 之后运行节点会有问题
- 出现问题的参考 issue：[Tracker does not move · Issue #4 · ZJU-FAST-Lab/Elastic-Tracker](https://github.com/ZJU-FAST-Lab/Elastic-Tracker/issues/4)
- 如果不使用 cuda 的话，就要在 `src/uav_simulator/local_sensing/CMakeLists.txt` 中进行修改，切换注释 `ENABLE` 选项。但是这样就没有办法使用深度图功能了，具体参考上面 issue

言归正传，最好还是配置好 cuda，那么这里要确定 3 个东西，分别是自己的显卡架构、cuda-tooklit 版本和 nvcc 编译选项
- 显卡架构：可以通过 `nvidia-smi -q`，然后查看输出的 `Product Attributes` 来确定
- cuda-tooklit 版本：可以通过 `nvcc --version` 来确定

首先要知道自己显卡的架构，然后以 NVIDIA XXX GPU Architecture Compatibility 为关键词查找到类似的官方网页，如 [NVIDIA Ada GPU Architecture Compatibility Guide](https://docs.nvidia.com/cuda/ada-compatibility-guide/index.html#building-applications-using-cuda-toolkit-11-8)

然后在这个网页中查看自己安装好的 cuda-tooklit 版本支持哪些 nvcc 编译选项
![](/document/Elastic-Tracker-Setup/assets-of-Elastic-Tracker-Setup/image-1.png)


然后看自己能够支持的 `nvcc` 编译器的选项，然后在项目的 `src/uav_simulator/local_sensing/CMakeLists.txt` 中修改 `CUDA_NVCC_FLAGS `
具体参考：
![](/document/Elastic-Tracker-Setup/assets-of-Elastic-Tracker-Setup/image-2.png)

之后再编译就可以看到正常的 GPU 渲染的等高颜色图了。

## 2. catkin_make 时编译的警告

yy 编译的时候会遇到警告，cmake 找不到 OpenCV、Boost 和 Eigen 的库，这个时候可以查看其中提示的源头 CMakelists.txt 文件，然后在其中添加 `find_package(OpenCV REQUIRED)`，`find_package(Boost REQUIRED)` 即可

好像不添加也没什么问题，只是会有一些警告？

