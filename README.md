# 3DOF Quadruped Robot

Inspired by Boston Dynamics' **Spot Mini**, this project implements a low-cost, open-source quadruped robot platform built on the **SpotMicroAI** architecture, with ROS2-based gait control and LiDAR-based obstacle awareness.

**Institution:** Mahindra University — Department of Mechanical and Aerospace Engineering
**Project Supervisor:** Dr. Deep Seth
**Team Members:**
- Sikhi Chintalapati (SE25MROB007)
- Yasho Ravali P. (SE25MROB006)
- Galla Rishi (SE25MROB005)

---

## 1. Introduction and Background

SpotMicroAI is an open-source quadruped robot inspired by Boston Dynamics' SpotMini, developed as a low-cost platform for robotics research and education. The robot uses:
- **3DOF legs** per limb
- **Servo motors** for actuation
- **Raspberry Pi** as the onboard compute
- **ROS integration** for control

It supports gait generation, walking, trotting, and inverse-kinematics experiments.

---

## 2. Literature Survey

| Robot / Research | Features | Limitation |
|---|---|---|
| Boston Dynamics Spot | Dynamic locomotion, obstacle climbing, autonomous navigation | Very expensive |
| Unitree Robotics Go1 | AI-based locomotion and vision system | Costly for research labs |
| MIT Mini Cheetah | High-speed running and backflips | Complex actuator design |
| ANYbotics ANYmal | Industrial inspection and terrain adaptability | High computational complexity |
| Stanford Doggo | Low-cost educational quadruped robot | Limited stability at high speed |
| ROS-based Quadruped Research | Modular simulation and easy integration | Requires high processing power |
| Reinforcement Learning-based Quadrupeds | Adaptive gait generation | Large training data required |
| Hydraulic Quadruped Robots | High load carrying capability | Heavy and expensive |
| SpotMicroAI | Open-source, low-cost quadruped platform | Limited payload capacity |

---

## 3. Technological Gap and Problem Statement

**Technological Gap:**
- High cost of existing quadruped systems
- Limited sensing integration in student-scale projects
- Difficulty in gait synchronization
- Lack of autonomous obstacle awareness

**Problem Statement:**
> Develop a low-cost quadruped robot capable of trot gait locomotion and LiDAR-based obstacle detection using ROS2.

---

## 4. Objectives

- Develop a quadruped robot platform
- Implement trot gait locomotion
- Interface servo motors using the **PCA9685** PWM driver
- Develop ROS2-based gait control
- Integrate the **RPLiDAR A2** sensor
- Implement autonomous **WALK / STOP** behavior

---

## 5. Mechanical Design and CAD

- CAD models of the robot frame and legs
- 3D-printed structural parts
- Leg assembly (3DOF per leg)

*(Slide reserved for CAD renders, printed-part photos, and leg-assembly images.)*

---

## 6. Hardware Architecture

| Component | Role |
|---|---|
| Raspberry Pi 4 | Main onboard compute / ROS2 host |
| Servo Motors | Joint actuation (3DOF per leg) |
| PCA9685 | PWM servo driver / channel mapping |
| RPLiDAR A2 | 2D obstacle scanning |
| Bluetooth Controller | Manual/remote control input |
| Battery | Onboard power supply |
| 3D-Printed Legs | Structural leg components |

---

## 7. Experimentation: Servo Testing

- Servo calibration (neutral angle calibration)
- PCA9685 setup and PWM channel mapping
- Joint synchronization across legs
- Power testing under load
- Wiring setup validation

---

## 8. Software Architecture

ROS2-based pipeline for perception-to-actuation:

```
/scan
  ↓
lidar_decision.py
  ↓
/gait_mode
  ↓
lidar_walk.py
  ↓
/joint_states
  ↓
all_leg_servo_driver.py
  ↓
Servo motors
```

**Key characteristics:**
- Built on **ROS2 Humble**
- Python-based ROS2 nodes
- Real-time topic-based communication
- Joint-space gait control

---

## 9. Experimentation: LiDAR Testing

- RPLiDAR A2 integration and driver setup
- Real-time scan acquisition via the `/scan` topic
- Obstacle-detection testing
- WALK/STOP behavior validation using LiDAR feedback

---

## 10. Experimental Results

**Locomotion Results:**
- Stable trot gait achieved
- Walking motion demonstrated
- Servo synchronization verified

**LiDAR Integration Results:**
- Real-time LiDAR scan acquisition
- Obstacle detection achieved
- Autonomous WALK/STOP behavior verified

---

## 11. Challenges Faced

- Balance issues (attributed to 3D-printed part tolerances)
- Leg/servo synchronization difficulties
- Mechanical instability
- Power fluctuations

---

## Summary

This project demonstrates a low-cost, 3DOF-per-leg quadruped robot (based on the SpotMicroAI open-source platform) running on a Raspberry Pi 4 with ROS2 Humble. Servo actuation is handled through a PCA9685 PWM driver, and an RPLiDAR A2 provides real-time obstacle sensing, enabling autonomous WALK/STOP behavior on top of a stable trot gait. The work targets the gap between expensive commercial quadrupeds (Boston Dynamics Spot, Unitree Go1) and accessible research/education platforms.
