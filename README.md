#include <Servo.h>

const int rainSensorPin = 2; // Digital pin connected to Rain Drop Sensor DO
const int servoPin = 9;      // PWM pin connected to Servo Motor signal

Servo clothesServo;

// Variables for State Tracking and Debouncing
bool isRaining = false; 
bool currentlyRaining = false;
unsigned long rainStartTime = 0;
const unsigned long debounceDelay = 3000; // Require 3 seconds of continuous rain to trigger

void setup() {
  pinMode(rainSensorPin, INPUT);
  clothesServo.attach(servoPin);
  clothesServo.write(0); // Initial position (clothes outside / under the sun)
  Serial.begin(9600);
}

void loop() {
  // Read the sensor (LOW usually means rain is detected)
  int sensorReading = digitalRead(rainSensorPin);
  
  if (sensorReading == LOW) {
    // If we just detected rain for the first time, start the timer
    if (!currentlyRaining) {
      currentlyRaining = true;
      rainStartTime = millis();
    }
    
    // Check if it has been raining continuously for the debounce delay (3 seconds)
    if (currentlyRaining && !isRaining && (millis() - rainStartTime >= debounceDelay)) {
      isRaining = true;
      Serial.println("Rain confirmed! Pulling clothes inside...");
      clothesServo.write(90); // Retract clothes
    }
  } else {
    // Weather is clear
    currentlyRaining = false;
    
    // Only move the servo if it was previously raining
    if (isRaining) {
      isRaining = false;
      Serial.println("Weather is clear. Extending clothes...");
      clothesServo.write(0);  // Extend clothes
    }
  }
  
  delay(100); // Small delay for stability
}
