# TOOP18 Turns and Bump sensor
This class will focus on making precise turns and utilizing the bump sensors.

## References
- [Pololu Motor Library Documentation](https://pololu.github.io/pololu-3pi-plus-32u4-arduino-library/class_pololu3pi_plus32_u4_1_1_motors.html)
- [Pololu IMU Library Documentation](https://pololu.github.io/pololu-3pi-plus-32u4-arduino-library/class_pololu3pi_plus32_u4_1_1_i_m_u.html)
- [Pololu Bump Sensor Library Documentation](https://pololu.github.io/pololu-3pi-plus-32u4-arduino-library/class_pololu3pi_plus32_u4_1_1_bump_sensors.html)

## Making precise turns
Last class we were able to utilize the IMU and turnsensor.h to display a heading.  Now we can combine the two to make precise turns.  The pseudocode below is a good starting point when writing a function that can execute a precise 90 degree clockwise turn.

![image](https://github.com/CGA-TOOP/TOOP18/assets/67393204/1f9d0eda-ea8d-4ba0-931a-c7c10b591d1b)

## Working with the bump sensor
The 3pi+ 32U4 includes two bump sensors on the front of the robot.  To utilize the bump sensors, we must include the Pololu library `#include <Pololu3piPlus32U4.h>`.  We also must create a bump sensors object from the `BumpSensors` class:

`BumpSensors bumpSensors`

The status of the bump sensor can be determined a few different way.  You can call the `read()` function to return a two bit value indicated the status of the left and right bump sensor, where bit 0 is the status of the right sensor and bit 1 is the status of the left sensor. For example, a return value of 2 (0b10 in binary) indicates:

  - The right bump sensor is pressed, since bit 1 (BumpRight) is set.
  - The left bump sensor is not pressed, since bit 0 (BumpLeft) is cleared.

Instead of checking the return value of this method, you can instead call `read()` and then use the functions `leftChanged()`, `rightChanged()`, `leftIsPressed()`, and `rightIsPressed()` to get information about the bump sensors.

Here are some of the commands you may frequently use:
```
void calibrate()  //calibrated the bump sensors
uint8_t read()  //Reads both sensors
void leftChanged()  //Indicates a state change of left bump sensor since last read
void rightChanged()  //Indicates a state change of right bump sensor since last read
void leftisPressed() //Indacates left bump sensor is pressed
void rightisPressed() //Indacates right bump sensor is pressed
```

## Exercise
Begin today’s in-class exercise by using the pseudocode above to create a funciton that can execute a 90 degree coutner clockwise turn.

After that, make a new Platform IO project named TOOP17 and program your robot to meet the following requirements. The goal is for when your code starts, the robot waits for a button press. If button A is pressed, the robot will move forward until it hits an obstruction. If button B is pressed, your robot will execute a 90 degre clockwise turn.  If time allows, have your robot make a 90 degree counter clockwise turn if butotn C is pressed.

In setup() 
  - Initialize the display, and turnsensor.
  - Display “Motors Ready” 
  - Calibrate the bump sensors
  - Display on the second line of the OLED “Bumpers ready”

In loop() 
  - Using a switch statement to do the following:
    - If button 1 is pressed, start the motors so your robot moves forward untill your robot hits an obstruction
    - If button 2 is pressed, execute a 90 degree clockwise turn.
  - Delay for .5 second 

Please refer to previous in class exercises for the getButton() function (or copy from your previous code!). 

 

 





