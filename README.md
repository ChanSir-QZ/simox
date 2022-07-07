# simox
## Introduction

  轻量级平台独立 C++ 工具箱 Simox 的目的是为机器人系统的 3D 仿真、基于采样的运动规划和抓取规划提供一套算法。Simox 由三个库（Virtual Robot、Saba 和 Grasp Studio）和大量示例组成，
  这些示例展示了如何使用这些库在移动操作的环境中构建复杂的工具。Virtual Robot库可用于定义复杂的机器人系统，它可能涵盖多个具有多个自由度的机器人。机器人结构及其可视化可以通过 XML 文
  件轻松定义，并且支持带有障碍物和对象的环境。此外，Virtual Robot库也提供了基本的机器人仿真组件，如雅可比计算和通用逆运动学 (IK) 求解器。除此之外，Saba 提供了一个用于规划无碰撞运动
  的库，该库直接与 Virtual Robot 提供的数据相结合。这些算法涵盖了基于采样的运动规划方法（例如快速探索随机树）的最新实现以及允许方便地实现自己的规划器的接口。由于 Saba 是为在高维配
  置空间中进行规划而设计的，因此可以有效地解决具有高自由度 (DoF) 的机器人的复杂规划问题。Grasp Studio 提供了计算通用末端执行器定义（例如人形手）的抓握质量的可能性。实施的 6D 扳手空
  间计算可用于轻松（快速）确定对对象应用抓取的质量。此外，实施的规划器能够自动生成给定对象的抓取图。由于复杂的框架必须与多个库合并才能提供完整的功能，因此在设置环境时可能会出现一些问
  题，例如依赖性问题、不兼容的库版本甚至所用操作系统所需库的不存在端口。因此，Simox 核心仅使用一组有限的库来使其编译。可以关闭扩展功能（例如可视化）以允许在大多数平台上编译 Simox。
  进一步的依赖被封装在接口中，使得交换变得容易，例如碰撞引擎或可视化功能。作为参考实现，Simox 提供基于 Coin3D/SoQt 的可视化支持。





## Installation on Ubuntu18.04 

### Get Simox from gitlab repository
Retrieve the sources with:

`git clone https://gitlab.com/Simox/simox.git`

### Install Dependencies
On Ubuntu 18.04 execute the following lines:
```
sudo apt-get install -y curl apt-file
sudo curl https://packages.humanoids.kit.edu/h2t-key.pub | sudo apt-key add - 
echo -e "deb http://packages.humanoids.kit.edu/bionic/main bionic main\ndeb http://packages.humanoids.kit.edu/bionic/testing bionic testing" | sudo tee /etc/apt/sources.list.d/armarx.list 
sudo apt-file update
#simox dependencies
sudo apt install -y git g++-8 libboost-all-dev cmake libeigen3-dev libnlopt-dev freeglut3-dev qtbase5-dev libqhull-dev  liburdfdom-dev libassimp-dev libtiff-dev
sudo apt-get install h2t-libbullet h2t-libsoqt5-dev h2t-libsimage-dev h2t-libcoin80-dev
```

### Compile Simox
On Ubuntu 18.04:

Create make files:

```
cd simox  
mkdir build  
cd build  
CXX=g++-8 cmake ..  
make -j4
```

You may need to adapt your bullet path.
