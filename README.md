# Rain Detection-Based Automatic Clothes Collector System 🌧️👕

An Arduino Uno-powered smart home automation project designed to automatically protect your laundry from sudden rain by retracting or sheltering them using a servo motor mechanism.

## 🛠️ Components Required
1. Arduino Uno
2. Arduino Uno Cable (USB)
3. Rain Drop Sensor Module
4. Servo Motor (e.g., SG90 or MG995)
5. Mini Breadboard
6. Male-to-Male & Male-to-Female Jumper Wires

## 🔌 Circuit Connections / Wiring Guide

### Rain Drop Sensor to Arduino Uno:
* VCC -> Uno 5V
* GND -> Uno GND
* DO (Digital Out) -> Uno Digital Pin 2

### Servo Motor to Arduino Nano:
* VCC (Red) -> Arduino Nano `5V` 
* GND (Brown/Black) -> Arduino Nano `GND`
* Signal (Orange/Yellow) -> Arduino Nano `D9`

## 💻 Arduino Code
Upload the code located in the `code/` folder using the [Arduino IDE](https://www.arduino.cc/en/software). Make sure to select **Arduino Uno** as your board and the correct processor/COM port.
