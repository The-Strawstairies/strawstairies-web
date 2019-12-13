---
title: "Electrical"
layout: PostLayout
date: 2019-12-14
emoji: 📯
---

# Electrical Requirements
* An Arduino for central computing and controls
* Angular velocity and linear acceleration sensing for balance control relative to gravity
* Servo to control balance offset
* Motor controllers and fuses to control 2 20A max stall current draw motors operating at 12VDC, specced for 25lb stair climbing at worst case conditions
* Wireless communication to the robot for teleoperated control of the robot's motion from a keyboard
* Sourcing a battery that can power all the different components

The electrical schematic for this system is shown below.
<img src="./schem.png" alt="schematic" width="2000"/>

# General Description
To read more about the reasoning behind our decisions, see the *Process and Components* section below.
## Power
In the schematic, we can see on the left side that we have a 5V phone battery pack, an 11.1V lipo battery, and power input into an Arduino Motor Shield to take in the 11.1V battery input. From there, we can power the Arduino, which can power most other 5V devices such as the Servo and inertial measurement unit (IMU), which contains an accelerometer and gyroscope. The 11.1V lipo also powers the motor controllers on the right side of the schematic which power and control the drive motors. Since the motors could potentially draw a peak voltage that we don't expect, we incorporated a 50A fuse between the lipo battery and the 2 motor controllers to ensure that we wouldn't burn out any motors or motor controllers. Meanwhile, the 5V battery pack charged the Raspberry Pi since it draws too much current for the Arduino to power along with the other components. 
## Communications
The sole purpose of the Raspberry Pi is for wifi connection to a computer for teleoperated control. From there, it connects to the Arduino via serial to control the systems based on user input.
### Balance
The Arduino connects to the IMU via I2C and has an interupt pin to constantly be pulling information back from the IMU based on interupts to process the orientation of the robot from accelerometer and gyroscope data. From there, the Arduino sends a PWM signal to the servo motor to counteract the orientation of the robot in one axis an always have the balance board parallel to the ground. 
### Drive
The Arduino also sends a PWM signal to both motor controllers which then drive the motors on either side of the robot. 

# Process and Components
As for our process, there were a few givens and then a few decisions we could have made when approaching electrical design. With the mechanical specifications based on torque of the whegs, we needed pretty powerful motors, a servo to physically offset the balance based on a sensor and we needed an Arduino to control them and the balancing component of our system. We then worked backwards to source motor controllers that were rated for 20A continuous output to power the drive motors and an integrated inertial measurement unit (IMU) that contained the accelerometer and gyroscope necessary for sensing the orientation of the robot in real time. We then knew we were going to need some way to connect wirelessly and we chose to use a Raspberry Pi for Wifi communication instead of a Bluetooth module for Arduino for a few reasons. For one, the Raspberry Pi was cheaper than a Bluetooth module, and secondly, we liked that with a Raspberry Pi, we could write software to enable anyone on a specific Wifi network to connect to the robot from anywhere. 

From there, we had all of our non-battery components and could figure out how to power the system. We needed a near-12VDC battery to power motor controllers and drive motors, but we also needed a 5V power supply for the Arduino, Raspberry Pi, IMU, and servo. To avoid a voltage stepdown, we used an Adafruit Arduino Motor Shield which has a built in voltage stepdown from 12VDC to 5VDC. We used this to power everything on the 5V rail except for the Raspberry Pi which draws too much current for the Arduino to handle along with the other supplies. We then strapped a 5V phone battery charger onto the robot to power the Raspberry Pi. Finally, we just had to wire everything up and make sure it all worked (spoiler alert: it did!). Because of our carefullness with fuses and calculations for what we expected the current draws to be, we didn't burn anything out :)

<!-- more -->