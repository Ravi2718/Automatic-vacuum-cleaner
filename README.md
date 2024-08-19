# Auto-Cleaning Robot

## Overview

This project involves the creation of an Auto-Cleaning Robot using Arduino. The robot is equipped with ultrasonic sensors to detect obstacles and a servo motor to control movement direction. The robot can move forward, reverse, turn left, and turn right based on sensor readings. The robot's actions are displayed on an LCD, and a motor driver (L293D) is used to control the motors.

## Components Required

1. **Arduino Board**: To control the robot.
2. **Ultrasonic Sensors**: For obstacle detection.
   - Front Sensor: Connected to pins `A4` (Trig) and `A5` (Echo).
   - Back Sensor: Connected to pins `13` (Trig) and `12` (Echo).
3. **Servo Motor**: Connected to pin `9`, used for scanning the environment.
4. **L293D Motor Driver**: To drive the motors.
   - Motor 1: Connected to pins `A3` (in1) and `A2` (in2).
   - Motor 2: Connected to pins `A1` (in3) and `A0` (in4).
5. **LCD Display**: 16x2 LCD to display the robot's status, connected to the Arduino via `LiquidCrystal` library.
6. **Relay Module**: Connected to pin `11`, used to control the power to the motors.

## Pin Configuration

- **Servo Motor**: Pin `9`.
- **Ultrasonic Sensors**:
  - Front Sensor: `Trig` pin on `A4`, `Echo` pin on `A5`.
  - Back Sensor: `Trig` pin on `13`, `Echo` pin on `12`.
- **Motor Driver (L293D)**:
  - Motor 1: `in1` on `A3`, `in2` on `A2`.
  - Motor 2: `in3` on `A1`, `in4` on `A0`.
- **Relay Module**: Pin `11`.
- **LCD**:
  - `RS`: Pin `2`
  - `EN`: Pin `3`
  - `D4`: Pin `4`
  - `D5`: Pin `5`
  - `D6`: Pin `6`
  - `D7`: Pin `7`

## How It Works

1. **Setup**:
   - The servo motor scans from 0 to 180 degrees and back to 0 degrees to detect obstacles using the ultrasonic sensors.
   - The robot's movement is controlled based on the distance measured by the ultrasonic sensors.

2. **Movement**:
   - **Forward**: If both the front and back sensors detect no obstacles within 20 cm.
   - **Reverse**: If both sensors detect obstacles within 20 cm.
   - **Turn Right**: If only the front sensor detects an obstacle.
   - **Turn Left**: If only the back sensor detects an obstacle.
   - **Stop**: When both sensors detect obstacles, the robot stops before reversing and turning.

3. **LCD Display**:
   - Displays "Auto-Cleaning Robot" on startup.
   - Continuously updates the status during operation.

4. **Serial Monitor**:
   - Outputs the distance readings from the sensors.
   - Logs the robot's actions (forward, reverse, left, right, stop).

## Code Explanation

- **Initialization**: In the `setup()` function, the pins are configured, the servo is attached, and the LCD is initialized.
- **Loop**: The robot continuously scans the environment, updates sensor readings, and decides the movement based on sensor data.
- **SonarSensor Function**: Calculates the distance to the nearest object using the ultrasonic sensors.
- **Movement Functions**: Control the direction of the robot by setting the appropriate pins on the L293D motor driver.

## Usage

1. Assemble the components as per the pin configuration.
2. Upload the provided Arduino code to the Arduino board.
3. Power up the robot, and it will start scanning and moving based on the detected obstacles.

## Notes

- Ensure the ultrasonic sensors are properly aligned to accurately detect obstacles.
- Adjust the `delay` values if the robot's movements need fine-tuning.

## Troubleshooting

- If the robot doesn't move correctly, check the wiring of the motor driver.
- Verify that the servo motor is functioning correctly by checking its movement during startup.
- Ensure that the ultrasonic sensors are correctly connected and functioning by observing the distance readings on the Serial Monitor.
