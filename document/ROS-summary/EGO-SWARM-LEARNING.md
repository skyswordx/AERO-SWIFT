
# EGO-Swarm 项目的学习

Author:@skyswordx(袁越), ...  
Date:2025.2.7

## 参考链接

- [EGO_planner代码中的状态机 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/570040122)
- [EGO-Planner论文阅读笔记 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/366372048)

## EGO-Swarm 的节点图整理

![EGO-Swarm 的节点图整理](assets-of-EGO-SWARM_LEARNING/image-0.png)


从节点图的整理来看，我们要把这个项目部署到真机，主要需要注意的接口为：
1. `ego_planner_node` 接收外部传感器的数据：无人机位姿和点云信息，更细致一点来说是由 `GridMap` 类接收外部传感器的数据，可以选择深度相机或者激光点云，相机位姿或机体位姿）
2. `traj_server` 向无人机发送控制指令

于是下面关注接口节点的具体实现，这两个节点都位于项目源码的 `/planner/plan_manage/` 部分
```shell
. # EGO-Swarm 源码根目录
├── planner # EGO-Swarm 规划器，包含节点和依赖库实现
│      ├─ bspline_opt
│      ├─ drone_detect
│      ├─ path_searching
│      ├─ plan_env
│      ├─ rosmsg_tcp_bridge
│      ├─ traj_utils
│      └─ plan_manage # 负责 ego-planner\traj_server 两个节点
└── uav_simulator # 仿真环境的节点实现
```


## Fast-Drone 调参

启动文件
- 地图大小
- 膨胀和分辨率
- 最大速度

px4ctrl 的 config 文件
- 实际飞机参数
- 遥控通道是不是反的
- `hover_percentage` 自动收敛的值

## 参考链接

- [Longer95479/Fast-Drone-XI35](https://github.com/Longer95479/Fast-Drone-XI35?tab=readme-ov-file#5-%E4%BB%A3%E7%A0%81%E7%BC%96%E8%AF%91%E4%B8%8E%E5%90%AF%E5%8A%A8%E6%B5%81%E7%A8%8B)
- [高飞组-PX4控制器讨论及分析 - 知乎](https://zhuanlan.zhihu.com/p/638635777)
- [aphasiayc/px4ctrl: Fork from ZJU-FAST-LAB/Fast-Drone-250](https://github.com/aphasiayc/px4ctrl?tab=readme-ov-file#%E6%8F%90%E9%AB%98%E7%B2%BE%E5%BA%A6%E6%80%BB%E7%BB%93)
- [【东北大学REAL实验室】自主无人机组装教学视频 - 4 PX4_Ctrl FSM讲解与真机定点飞行_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV11i421y7ta/?vd_source=a901441d2c723973826f98ab4b1463a5)
- [NEU-REAL/REAL_DRONE_400: An open source Drone Suite for Aerial Robot](https://github.com/NEU-REAL/REAL_DRONE_400) 
- 

