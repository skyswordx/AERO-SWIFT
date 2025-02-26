# MISSION-10   
FOR IARC
---

这个仓库的作用是为了记录我们空队推进相关比赛的项目进度，以及我们的讨论结果

努力做到每周来总结一下进度和已完结的讨论结果。对于整个仓库，每个人都是 collaborator，可以积极地 contribute

这个仓库建立的目的是明确我们需要做什么、每个人应该做什么，记录我们做了什么，及其提供一个空间让每个人所做的事情汇在一起

---
**目录：**
1. ✌🏻 进度安排
2. 🎯 目前重点文档
3. 🤓 一些灵光一现 (idea)
4. 🤫 资料区
5. 💖 编写注意事项

---

## ✌🏻 进度安排

| 有效性 | 阶段   | 时间             | 备注    | 详细安排的文档链接                  |
| --- | ---- | -------------- | ----- | -------------------------- |
| ❌   | 准备阶段 | 2024.12-2025.1 | 寒假前工作 | [V1.0](./schedule/V1.0.md) |
| ❌   | 准备阶段 | 2024.12-2025.1 | 寒假前工作 | [V1.1](./schedule/V1.1.md) |
| ✔   | 准备阶段 | 2024.12-2025.1 | 寒假前工作 | [V1.2](./schedule/V1.2.md) |

每次的进度安排都会开会讨论决定，分为大方向和其细化过的小方向，大家一起来提！
- 大方向就是我们整个项目的推进方向了
- 细化的小方向是“为了完成大方向”我们现在缺什么、还需要做什么，这个大家有想到的 or 不赞同的强烈欢迎补充，小方向约细化越具体越好🧐
## 🎯 目前重点文档

- [PX4-ROS 相关学习资料](document/ROS-summary/PX4-ROS-LEARNING.md) 
- [EGO-Swarm 学习记录文档](document/ROS-summary/EGO-SWARM-LEARNING.md)

## 🤓 一些灵光一现 (idea)

突然想到的跟项目进度有关的任何小东西都欢迎丢过来！万一用上了呢😋

**idea 1**
- 先跟着 XTDrone 这个仿真平台的使用教程，熟悉一下 PX4-ROS 的使用方式
- 然后在自己的 XTDrone 上面复现 [XXLiu-HNU/Fast-Drone-250-v2:多机 Gazebo 仿真](https://github.com/XXLiu-HNU/Fast-Drone-250-v2)
- 理解上述项目使用 EGO-Swarm 的方法，并部署在 PX4 固件的真机
- **目前在文档 [PX4-ROS 相关学习资料](document/ROS-summary/PX4-ROS-LEARNING.md) 中已经准备好了相关流程的介绍和要做的事情**
- **剩余重点目标是基于 fastdrone 跑 EGO-Swarm 的 gazebo 仿真**

## 🤫 资料区

- [视频：无人机软硬件科普](https://www.bilibili.com/video/BV1Jq4y1T7QD?spm_id_from=333.788.videopod.episodes&vd_source=9c85d181a345808c304a6fa2780bb4da&p=2)
- [一些无人机硬件相关的关键词列表](./document/UAV-concepts/UAV-concepts.md)（要是用到了可以直接用关键词搜索）
- [PX4-ROS 相关学习资料](document/ROS-summary/PX4-ROS-LEARNING.md) 
- ~~[UE5.3-AirSim仿真环境搭建](./document/simulation-environment/UE5.3-AirSim-Environment.md)  关于 UE 5.3-AirSim 仿真环境搭建过程~~
- 无人机跟随参考的项目[Elastic-Tracker](https://github.com/ZJU-FAST-Lab/Elastic-Tracker) 相关的总结
	- [复刻使用 NVCC 编译时版本选项会遇到的一些问题](./document/GPU-Setup/CUDA-Toolkit-NVCC-options.md)
- 集群通信和规划参考的项目：[ego-planner-swarm](https://github.com/ZJU-FAST-Lab/ego-planner-swarm) 
	- 部署的 b 站视频：[【完结】从0制作自主空中机器人](https://www.bilibili.com/video/BV1WZ4y167me?spm_id_from=333.788.videopod.episodes&vd_source=9c85d181a345808c304a6fa2780bb4da)
	- 相关学习记录的文档：[EGO-Swarm 学习记录文档](document/ROS-summary/EGO-SWARM-LEARNING.md)
- batman-mesh 相关的链接
	- [openwrt-batman-tutorial](https://github.com/benkay86/openwrt-batman-tutorial)
	- [在 VMWare 中安装 OpenWrt | Shepherd's Blog](https://shepherd-xie.github.io/2024/09/26/deploy-openwrt-on-vmware/)
- [D435i配置教程](./document/D435i-tutorial/D435i-tutorial.md)
- [妙算 manifold-2C 配置经验](./document/Manifold-2C-Setup/Manifold-2C-Setup.md)
- IARC 任务规则细谈
	- 中文省流 [Rules](document/IARC-Rules/Rules.md)

## 💖 编写注意事项

1. 文件模版：[template](./template.md)
1. 每次提交的commit尽量具体
2. 执行 `git push` 操作前先执行 `git pull` 操作将远程仓库同步到本地
3. 不要使用`git push --force`命令进行提交
2. 文件名用英文名，不要有空格之类的
3. just do it！尽情编写，仓库自会有~~苦力~~来整理

