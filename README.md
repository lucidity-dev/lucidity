# lucidity

Lucidity is a minimal robotics framework built around nanomsg, protobuf, [bulletin](https://github.com/lucidity-dev/bulletin) and [lucid](https://github.com/lucidity-dev/lucid).



## Design

In lucidity you split your robotics project into multiple self contained services. For example, I have a robot with a controls service, sensor service, and a computer vision service. Each one of these services would subscribe and publish to certain topics exactly like in [ROS (Robot Operating System)](http://www.ros.org/). In lucidity instead of relying on a central message broker (roscore) you will use nanomsg for brokerless pub/sub. For data serialization, instead of using ROS msgs in lucidity we use protobufs. In all of this, bulletin is a service discovery tool that allows the services to find topics they can subscribe to and register topics they are publishing on. Finally, the lucid build tool allows you to orchestrate the starting of all these services and registers all the publishers with bulletin.

## Motivation

ROS is the standard for most robotics software in the world, but it has many limitations. When using ROS a developer is tied down to either Python or C++ rather than using the right technologies for a specific task. In addition, the roscore centralized broker becomes a bottle neck in many implementations at scale. The advantages of ROS are the community and the readily available packages, but eventually when people try to scale with ROS they move away from it or hack around it. The goal with lucidity is to make the framework minimal and lightweight and put as much control in the developers hands.



## Getting Started

### Prerequisites

- memcached
- protobuf
- golang

### Install Bulletin and Lucid

Clone both [bulletin](https://github.com/lucidity-dev/bulletin) and [lucid](https://github.com/lucidity-dev/lucid), and then follow the build instructions. Then run the example in lucid. For new projects follow the example as a template. 