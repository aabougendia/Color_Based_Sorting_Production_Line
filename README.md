
# Color-Based Sorting Production Line Project

## Overview

This project is a production line system designed to automate sorting tasks using a TCS3200 color sensor, IR sensors, servo motors, and a conveyor belt. It integrates advanced features such as a user interface, manual overrides, automatic error detection, and data logging. The project is implemented using the ATmega32 microcontroller.

## Features

- **Color Detection**: Utilizes the TCS3200 sensor with Timer0 and an external interrupt to detect object colors (red, green, blue).
- **Object Detection**:
  - An IR sensor identifies objects approaching the color sensor.
  - Three additional IR sensors, paired with SG90 servos and 3D-printed linear actuators to detect object movement near designated actuators.
- **Conveyor Belt Control**:
  - A DC motor, powered by PWM signals from Timer1, drives a 3D-printed conveyor belt.
  - The L298N DC motor driver ensures precise motor control.
- **User Interface**:
  - Operators can set sorting criteria (e.g., assigning specific colors to bins) via a keypad.
  - Displays system status, the number of objects sorted, and real-time error messages on an LCD.
- **Manual Override**:
  - Enables operators to pause the conveyor, override sorting, or shut down the system in emergencies.
- **Automatic Error Detection**:
  - Identifies sorting errors by tracking sorting times and using an IR sensor at the end of the belt to check for unsorted objects.
- **Routing Circuit**:
  - A 74139 dual 2-to-4 decoder routes PWM signals from Timer1 to the appropriate servo based on a 2-bit control signal.
  - A 74147 10-to-4 priority encoder converts signals from four IR sensors (three for servo proximity and one for error detection) into a 3-bit binary value for the microcontroller.
- **System Timing**:
  - Calculates time spent sorting and stores it in EEPROM memory.
- **Data Logging and Monitoring**:
  - Logs the number of sorted objects, sorting time, and error occurrences into EEPROM for performance analysis.
- **Alerts**:
  - LEDs indicate production line status (running, paused, or stopped due to errors).
  - A buzzer alerts the operator in critical situations.
- **Power Supply**:
  - A 9V power adapter powers the DC motor driver.
  - A 5V power supply powers the logic circuits.

## Components

- **Microcontroller**: ATmega32
- **Color Sensor**: TCS3200 with MCU Timer0 and EXTI0 to capture the color frequency and process it
- **IR Sensors**: Five IR sensors (one for color sensor proximity, three for the sorting mechanism, and one for error detection)
- **Servo Motors**: three SG90 180° servos with 3D-printed linear actuators
- **DC Motor**: 12v DC geared motor to drive the conveyor belt
- **Motor Driver**: L298N
- **Decoders and Encoders**:
  - 74139 dual 2-to-4 decoder
  - 74147 10-to-4 priority encoder
- **Power Supplies**:
  - 9V 1A power adapter
  - 5V 2A power supply
- **Display**: Character LCD for system status and error messages
- **Keypad**: 4x1 Keypad For operator input
- **Buzzer and LEDs**: Three LEDs and a 5v buzzer for system status and alerts
- **Additional Components**:
  - 0.47uF capacitor and a 1N4004 diode to rectify and smooth current fluctuations from the DC motor

## How It Works

1. An IR sensor detects an object approaching the TCS3200 color sensor.
2. The color sensor identifies the object's color (red, green, or blue).
3. Based on the detected color, the routing circuit directs PWM signals to the appropriate servo, moving the object to its designated bin.
4. A DC motor drives the conveyor belt with PWM signals ensuring precise speed.
5. Sorting errors are automatically detected and logged for analysis.
6. Operators interact with the system through the keypad and monitor the status and errors on the LCD.

## How to Use

1. Use the keypad to set sorting criteria and monitor the process on the LCD.
2. Place an object on the conveyor belt.
3. The system automatically detects the object's color and sorts it into the correct bin.

## License

This project is licensed under a proprietary license. The code and design may be viewed but not used, reproduced, or distributed without explicit permission.

## Contributors

- Abdulrahman Abougendia
- Jana Sherif
- Rokaya Radwan
