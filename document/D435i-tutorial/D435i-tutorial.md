# D435i 配置教程

Author：@liangbm3(梁倍铭)  
Date：2025.1.12

## 1. 驱动安装

摄像头官方文档：
https://dev.intelrealsense.com/docs/docs-get-started

驱动仓库：
https://github.com/IntelRealSense/librealsense

克隆驱动仓库（指定版本，踩过坑，驱动版本需要和固件相对应）
```bash
git clone -b v2.50.0 https://github.com/IntelRealSense/librealsense  
```
克隆可能会发生错误，可以直接在该页面下载压缩包：
https://github.com/IntelRealSense/librealsense/tree/v2.50.0

安装依赖：
```bash
sudo apt-get install libudev-dev pkg-config libgtk-3-dev
sudo apt-get install libusb-1.0-0-dev pkg-config
sudo apt-get install libglfw3-dev
sudo apt-get install libssl-dev
```

安装权限脚本(进入`librealsense-2.50.0`文件夹执行以下命令)：
```bash
sudo cp config/99-realsense-libusb.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules && udevadm trigger 
```

编译和安装：
```bash
mkdir build
cd build
cmake ../ -DBUILD_EXAMPLES=true
make
sudo make install
```

>如果编译过慢可以使用`make -j8`命令

测试：
```bash
realsense-viewer
modinfo uvcvideo | gr
```

>插入摄像头屏幕可能发生翻转：重启即可

**注意**：  
USB线必须使用3.0以上的，同时如果在虚拟机中需要将USB兼容性改为3.1，参考链接：<https://blog.csdn.net/qq_28872655/article/details/131452813>

显示如图界面则成功  
![alt text](./assets/image.png)

## 2. ROS接口安装

创建ROS工作区：
```bash
mkdir -p ~/realsense_ros_ws/src
cd ~/realsense_ros_ws/src
```

克隆仓库：
```bash
git clone https://github.com/IntelRealSense/realsense-ros.git
git clone https://github.com/pal-robotics/ddynamic_reconfigure.git
```

列出仓库中的所有标签，切换到2.x.x的最新版本：
```bash
cd realsense-ros/
git checkout `git tag | sort -V | grep -P "^2.\d+\.\d+" | tail -1`
```

初始化ROS工作区：
```bash
cd ../../
cd ~/realsense_ros_ws/src
catkin_init_workspace
```

进行编译：
```
cd ..
catkin_make clean
catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
catkin_make install
```

设置环境变量：
```bash
echo "source ~/realsense_ros_ws/devel/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

启动摄像头节点：
```bash
roslaunch realsense2_camera rs_camera.launch
```
此时可以用`rostopic`来查看相关话题  
其他内容自行参考如下链接学习：  
<https://github.com/IntelRealSense/realsense-ros/tree/2.3.2> 
## 3. 参考链接

+ [Melodic + Realsense D435i 配置及错误问题解决](https://blog.csdn.net/Hacker_MAI/article/details/107976049)
+ [Intel RealSense D435i:简介、安装与使用(ROS、Python)](https://zhaoxuhui.top/blog/2020/09/09/intel-realsense-d435i-installation-and-use.html)

