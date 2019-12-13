# Software Requirements
* Drive the robot with adjustable speed (C++) 
* Manage keyboard inputs to execute motion commands (Python)
* Manually balance wheg phase (C++)
* Process accelerometer and gyroscope inputs to calculate current angle of the robot and control the servo to counterbalance the robot angle and remain level to the ground (C++) 

# General Description
## Python
Once the user has connected to the Raspberry Pi, which has our code repository already flashed into the device, we run a Python script which handles the keyboard input using threading and termios, a Linux terminal I/O module that enables us to read command line inputs. This enables us to continuously check for inputs and add them to a thread which we can parse and use. We first get a key, then parse the input to see if it matches with any of the keys mapped to commands such as drive forward, backwards, or increase/decrease speed. From there, we have a serial connection from the Raspberry Pi this code is running on and the Arduino. We write the key command to the serial monitor and the C++ code on the Arduino handles the input to drive the robot based on these inputs. 
## C++


# Components and Process

# Controls
For simplicity, we used a WASD style interface to drive the robot where <kbd>T</kbd> drives forward, <kbd>G</kbd> drives backwards, <kbd>F</kbd> drives left and <kbd>H</kbd> drives right for phase alignment. Furthermore, for code safety, we have a start and stop command which are <kbd>S</kbd> and <kbd>E</kbd>, respectively. To increase the speed of the robot, you can input <kbd>.</kbd>, which increases the speed by 10%. Alternatively, <kbd>,</kbd> will decrease the speed by 10%. Speed control is done by a percentage of the maximum linear velocity. 

<kbd>Z</kbd>