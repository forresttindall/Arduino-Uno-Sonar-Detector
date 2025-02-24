# Arduino Sonar Visualization Project

![Arduino Sonar Visualization](https://raw.githubusercontent.com/forresttindall/arduino-sonar-visualization/main/images/sonar_demo.gif)

## Overview

This project combines an Arduino with an ultrasonic distance sensor and servo motor to create a functional radar-like system. The Arduino controls the servo rotation and distance measurements, while a Processing application visualizes the data in a clean, interactive radar display.

## Features

- 150° scanning range (from 15° to 165°)
- Real-time distance measurement up to 40cm
- Visual radar-style display with distance indicators
- Color-coded object detection
- Angle and distance measurements displayed on screen

## Hardware Requirements

- Arduino board (Uno or similar)
- HC-SR04 Ultrasonic sensor (or equivalent)
- Servo motor
- Jumper wires
- Breadboard (optional)
- USB cable for connecting Arduino to computer

## Software Requirements

- [Arduino IDE](https://www.arduino.cc/en/software)
- [Processing IDE](https://processing.org/download)
- Required libraries:
  - Arduino: Servo.h
  - Processing: Serial library (included with Processing)

## Circuit Diagram

```
Arduino    HC-SR04    Servo
-------    -------    -----
5V    ---> VCC        VCC
GND   ---> GND        GND
Pin 10 ---> TRIG
Pin 11 ---> ECHO
Pin 12 --------------> Signal
```

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/forresttindall/arduino-sonar-visualization.git
   ```

2. Open `sonar_arduino_code.cc` in the Arduino IDE and upload it to your Arduino board.

3. Check which serial port your Arduino is connected to (in Arduino IDE: Tools > Port).

4. Open `Sonar_Vizualizer.java` in the Processing IDE.

5. Update the serial port in the Processing code to match your Arduino's port:
   ```java
   myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600); // Change this to your port
   ```

6. Run the Processing sketch to start the visualization.

## Usage

Once both programs are running:

1. The servo will begin scanning automatically from 15° to 165° and back.
2. The Processing application will display a radar-like visualization.
3. Objects detected within 40cm range will appear as red lines on the display.
4. Current angle and distance measurements are shown at the bottom of the display.

## Customization

### Arduino Code

- Adjust the scanning range by modifying the min/max values in the `for` loops.
- Change the scanning speed by modifying the `delay(30)` value.
- Connect the ultrasonic sensor to different pins by updating `trigPin` and `echoPin` constants.

### Processing Code

- Adjust the display resolution in the `size(1200, 700)` function.
- Modify colors by changing RGB values in the various drawing functions.
- Adjust the maximum detection range by changing the condition in `if(iDistance<40)`.

## How It Works

1. **Arduino Side**:
   - The servo motor rotates from 15° to 165° and back.
   - At each angle, the ultrasonic sensor measures the distance to any object.
   - The Arduino sends this data to the serial port in the format "angle,distance."

2. **Processing Side**:
   - Reads the serial data and parses the angle and distance values.
   - Draws a radar display with distance arcs and angle lines.
   - Displays a moving scan line corresponding to the current servo position.
   - Shows detected objects as red lines at their corresponding angles and distances.

## Project Structure

```
arduino-sonar-visualization/
│
├── sonar_arduino_code.cc      # Arduino code for servo control and distance measurement
├── Sonar_Vizualizer.java      # Processing code for visualization
├── images/                    # Project images and demonstrations
│   └── sonar_demo.gif
├── schematics/                # Circuit diagrams and hardware setup
└── README.md                  # This file
```

## Contributing

Contributions are welcome! Feel free to submit a Pull Request.

## License

This project is open source and available under the [MIT License](LICENSE).

## Contact

Forrest Tindall - [forrest.tindall@gmail.com](mailto:forrest.tindall@gmail.com)

Project Link: [https://github.com/forresttindall/arduino-sonar-visualization](https://github.com/forresttindall/arduino-sonar-visualization)


