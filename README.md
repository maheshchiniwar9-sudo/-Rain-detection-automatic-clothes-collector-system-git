# 🌧️ Smart Auto-Retracting Clothesline (Arduino Uno)

An open-source smart home automation project that automatically protects your laundry from sudden rain. Powered by an Arduino Uno, this system uses a raindrop sensor to detect precipitation and triggers a servo motor to retract the clothesline under a shelter.

## ✨ Features
* **Real-time Rain Detection:** Instantly reacts to rainfall.
* **Debounce Logic (Anti-Jitter):** Requires 3 continuous seconds of rain detection before triggering to prevent false alarms from morning dew or random moisture.
* **State Tracking:** The motor only activates when the weather state changes, preventing motor burnout and jitter.
* **Auto-Reset:** Automatically extends the clothesline back into the sun once the weather clears.

## 🛠️ Hardware Requirements
* **Arduino Uno R3** (or compatible board)
* **Rain Drop Sensor Module** (with digital output comparator)
* **Servo Motor** (SG90 for miniature prototype, or MG995 for larger scale)
* **Jumper Wires** (M-M and M-F)
* **Breadboard**
* *Optional but recommended:* External 5V power supply for the servo motor to prevent Arduino brown-outs.

## 🔌 Wiring Diagram

### Rain Sensor
| Sensor Pin | Arduino Uno Pin |
| :--- | :--- |
| VCC | 5V |
| GND | GND |
| DO (Digital Out) | Digital Pin 2 |

### Servo Motor
| Servo Wire | Arduino Uno Pin |
| :--- | :--- |
| Red (Power) | 5V (or External 5V) |
| Brown/Black (Ground)| GND (Must share ground with Arduino) |
| Yellow/Orange (Signal)| Digital Pin 9 |

## 🚀 Installation & Setup
1. Clone this repository to your local machine:
   `git clone https://github.com/YOUR-USERNAME/Arduino-Smart-Clothesline.git`
2. Open the `src/smart_clothesline.ino` file in the **Arduino IDE**.
3. Go to **Tools > Board** and select **Arduino Uno**.
4. Go to **Tools > Port** and select the active COM port.
5. Click **Upload**.
6. Open the **Serial Monitor** (set to 9600 baud) to monitor weather state changes in real-time.

## 🔮 Future Upgrades
For a full-scale, real-world deployment, the following upgrades are recommended:
- Swap the servo motor for a **DC Motor with a Worm Gear** (driven by an L298N motor controller) to handle the heavy weight of wet clothes.
- Add physical **Limit Switches** to stop the motor exactly when the clothes are fully extended or retracted.
- Add an **Active Buzzer** to alert the household when the clothes are being brought inside.
