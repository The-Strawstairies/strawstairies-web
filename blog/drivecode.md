---
title: "Preliminary drive code"
layout: PostLayout
date: 2019-10-31
emoji: 🛒
---

It's Halloween today, and the drive code just got some new features! We made a lot of changes which improve the code structure and performance of the system, but additionally, we added adjustments to fit our current design — a two motor drive train. Currently, turning, forwards movement, backwards movement, system stop, system reset, and speed adjustment are possible. We also have configured our own PID controller for future integration with sensors.

In a previous iteration of the design, we presumed that the optimal option would be a four motor system. However, due to budget limitations, worries about power usage, and the potential for sync issues, we switched to a two motor system.  In this pivot, each side of the robot gets one motor, i.e. a left drive and a right drive. This gives us a similar configuration to a tank drive, and allows for efficient forward movement and less efficient but possible rotational movement. In order to turn, dragging some of the wheels on the ground is required, but should be possible.   

-Dieter