# HuskyLens-AI-Welcome-System
An AI-powered object and face recognition welcome indicator using Arduino UNO, HuskyLens (via I2C), and LED status alerts.

# HuskyLens AI-Powered Welcome System 🤖📷

## Project Overview
This project is an AI-powered machine vision indicator built with Arduino UNO and the DFRobot HuskyLens. It uses onboard facial and object recognition to classify targets in real-time. Designed as a practical hardware integration and embedded systems task, the system operates autonomously without needing complex external computing. 

- **Known Target Detected:** Activates a Green LED.
- **Unknown Target Detected:** Activates a Red LED.

<img width="960" height="1280" alt="Huskeylens" src="https://github.com/user-attachments/assets/c1ada640-ff40-4a96-85da-cee01224cb6d" />


## 🛠️ Hardware Requirements
- Arduino UNO (or compatible standard board)
- DFRobot HuskyLens AI Camera
- 4-Pin JST Cable (for I2C communication)
- 2x LEDs (1 Green, 1 Red)
- 2x 220-ohm Resistors
- Breadboard & Jumper Wires

## 🔌 Circuit & Wiring Diagram
The camera communicates with the Arduino via the **I2C protocol**, ensuring an efficient and clean wiring setup.

| HuskyLens Pin | Arduino UNO Pin | Function |
| :---: | :---: | :--- |
| **VCC** (Red) | `5V` | Power Supply |
| **GND** (Black) | `GND` | Common Ground |
| **SDA** (Blue/Green) | `A4` | I2C Data Line |
| **SCL** (Green/Yellow) | `A5` | I2C Clock Line |

*Note: The Green LED is connected to Digital Pin `8` and the Red LED to Digital Pin `9`, both protected by 220-ohm resistors.*

<img width="960" height="1280" alt="Huskeylens Circuit Connection" src="https://github.com/user-attachments/assets/6366381d-061c-4d94-80d7-ee539487ca80" />


## 💻 Setup & Installation

1. **HuskyLens Configuration:**
   - Navigate to `General Settings` on the HuskyLens screen.
   - Change the `Protocol Type` to **I2C**.
   - Use the onboard buttons to "Learn" a face or an object (This assigns it `ID 1`).

2. **Install the HuskyLens Library (via ZIP):**
   - Download the `HuskyLens_Library.zip` file included in this repository.
   - Open the Arduino IDE.
   - Go to `Sketch` -> `Include Library` -> `Add .ZIP Library...`
   - Select the downloaded ZIP file to install it.

3. **Upload the Firmware:**
   - Connect your Arduino UNO via USB.
   - Compile and upload the provided `.ino` sketch.
   - Open the Serial Monitor at `115200` baud rate to view real-time detection logs.

## 🚀 How It Works (Code Logic)
The firmware continuously requests data blocks from the HuskyLens via I2C:
- If a target is recognized, HuskyLens returns an `ID > 0`. The Arduino triggers the **Green LED** and prints a welcome message.
- If a target is detected but not recognized (not learned), HuskyLens returns `ID = 0`. The Arduino triggers the **Red LED** to indicate an unknown entity.

## 🎥 Demonstration
*Watch the system in action as it dynamically switches LED indicators based on face recognition:*



https://github.com/user-attachments/assets/3d406f98-3f34-40b5-8d74-abed96d04f76

