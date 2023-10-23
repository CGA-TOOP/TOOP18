# TOOP18 Turns and Bump sensor
This class will focus on making precise turns and utilizing the bump sensors.

## References
- [Pololu Motor Library Documentation](https://pololu.github.io/pololu-3pi-plus-32u4-arduino-library/class_pololu3pi_plus32_u4_1_1_motors.html)
- [Pololu IMU Library Documentation](https://pololu.github.io/pololu-3pi-plus-32u4-arduino-library/class_pololu3pi_plus32_u4_1_1_i_m_u.html)
- [Pololu Bump Sensor Library Documentation](https://pololu.github.io/pololu-3pi-plus-32u4-arduino-library/class_pololu3pi_plus32_u4_1_1_bump_sensors.html)

## Making precise turns
Last class we were able to utilize the IMU and turnsensor.h to display a heading.  Now we can combine the two to make precise turns.  The pseudocode below is a good starting point when writing a function that can execute a precise 90 degree clockwise turn.

![image](https://github.com/CGA-TOOP/TOOP18/assets/67393204/1f9d0eda-ea8d-4ba0-931a-c7c10b591d1b)

## Working with the IMU (Inertial Measurement Unit)
The 3pi+ 32U4 includes on-board inertial sensors that allow it to determine its own orientation by implementing an inertial measurement unit (IMU). The first chip, an ST LSM6DS33, combines a 3-axis accelerometer and 3-axis gyro into a single package. The second chip is an ST LIS3MDL 3-axis magnetometer.
To utilize the IMU working we have to explicitly include the Pololu IMU library `#include <Pololu3piPlus32U4IMU.h>`.  We also must create an IMU object from the `IMU` class:

`IMU imu`

Working direclty with the IMU library can be a bit cumbersome.  To assist, you will want to utilize the provided TurnSensor.h header file.  Download this file and save in the `include` drectory of your PlatformIO project.  The purpose of this file is to allow you use predefined functions in your main.cpp to better control the gyro heading sensor. After you have created your objects, then be sure to include the TurnSensor.h file. 

Here are some of the command you may frequently use:
```
void turnSensorSetup()  //This should be called in setup() to calibrate your robot. 
void turnSensorReset() //This resets the starting point for measuring a turn.
void turn SensorUpdate()  //This reads the gyro and updates the heading.
```

## Putting it all together
Here is a basic starting point for future projects that need to use buttons, display, motors, and IMUs.
```
#include <Arduino.h>
#include <Pololu3piPlus32U4.h>
#include <Pololu3piPlus32U4IMU.h>

using namespace Pololu3piPlus32U4;

OLED display;
ButtonA buttonA;
ButtonB buttonB;
ButtonC buttonC;
Motors motor;
IMU imu;

#include "TurnSensor.h"

void setup(){

}

void loop(){

}

```
## Exercise
Begin today’s in-class exercise by cusing the pseudocode above to create a funciton that can execute a 90 degree coutner clockwise turn.

After that, make a new Platform IO project named TOOP17 and program your robot to meet the following requirements. The goal is for when your code starts, the robot waits for a button press. If button A is pressed, the robot will move forward until it hits an obstruction. If button B is pressed, your robot will execute a 90 degre clockwise turn.  If time allows, have your robot make a 90 degree counter clockwise turn if butotn C is pressed.

In setup() 
  - Initialize the display, and turnsensor.
  - Display “Motors Ready” 
  - Calibrate the bump sensors
  - Display on the second line of the OLED “Bumpers ready”

In loop() 
  - Declare an integer variable named buttonPressed which receives the returned value of the getButton function (code previously provided)
  - Using a switch statement evaluate buttonPressed and do the following:
    - If button 1 is pressed, start the motors so your robot moves forward, repeatedly display the range to an obstruction and continue moving forward until the ultrasonic sensor is less than or equal to 15 cm
    - If button 2 is pressed, start the motors so your robot moves backwards, display the repeatedly display the range from an obstruction and continue moving backwards until the ultrasonic sensor read 30.5 cm or more.
  - Delay for .5 second 

 

Please refer to previous in class exercises for the getButton() function (or copy from your previous code!). 

 

 





