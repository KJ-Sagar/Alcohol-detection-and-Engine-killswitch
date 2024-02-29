# Alcohol-detection-and-Engine-killswitch
A demonstrative system to check the possibility to prevent drunk driving and a proof of concept build
# Alcohol Detection and Engine Killswitch

An Arduino-based project to detect alcohol levels using the MQ9 alcohol sensor and activate an engine killswitch if the levels exceed a certain threshold.

## Table of Contents

- [Introduction](#introduction)
- [Components](#components)
- [Circuit Diagram](#circuit-diagram)
- [Installation](#installation)
- [Usage](#)

## Introduction

This project has been initiated as a proof of concept for an alcohol detection system to work on a larger project and further improve its implementation

## Components

List the components used in your project.

- Arduino Uno R3
- MQ3B Alcohol Sensor
- L298N Motor Driver
- Software kill switch
## Circuit Diagram

Include a simple circuit diagram to help users understand the wiring.

![Circuit Diagram]([https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUQGtOL21fQJ7RN4N0FwObe9H3bnQ8MMcvR8AtCca3qsJOVSPPYC_Ci9yk-w&s](https://www.google.com/url?sa=i&url=https%3A%2F%2Fnevonprojects.com%2Farduino-based-alcohol-sense-engine-lock-gps%2F&psig=AOvVaw3h5-SHb0PBu1r3GvgQrwqw&ust=1709281153722000&source=images&cd=vfe&opi=89978449&ved=0CBMQjRxqFwoTCMC3zKiP0IQDFQAAAAAdAAAAABAE)https://www.google.com/url?sa=i&url=https%3A%2F%2Fnevonprojects.com%2Farduino-based-alcohol-sense-engine-lock-gps%2F&psig=AOvVaw3h5-SHb0PBu1r3GvgQrwqw&ust=1709281153722000&source=images&cd=vfe&opi=89978449&ved=0CBMQjRxqFwoTCMC3zKiP0IQDFQAAAAAdAAAAABAE)

## Installation

Describe how to set up the hardware and install any necessary libraries or dependencies.

Example:

## CODE2. Arduino Code:

```arduino
#include <MQUnifiedsensor.h>

// Define alcohol sensor pin
int alcoholSensorPin = A0;

// Define motor driver pins
int motor1Pin = 9; // Connect to input 1 of L298N
int motor2Pin = 10; // Connect to input 2 of L298N

// Define alcohol threshold
int alcoholThreshold = 500;

void setup() {
  // Setup alcohol sensor
  MQUnifiedsensor alcoholSensor(alcoholSensorPin);
  alcoholSensor.begin();
  
  // Setup motor driver
  pinMode(motor1Pin, OUTPUT);
  pinMode(motor2Pin, OUTPUT);
}

void loop() {
  // Read alcohol level
  MQUnifiedsensor alcoholSensor(alcoholSensorPin);
  float alcoholLevel = alcoholSensor.alcoholRead();

  // Print alcohol level to serial monitor
  Serial.print("Alcohol Level: ");
  Serial.println(alcoholLevel);

  // Check if alcohol level exceeds threshold
  if (alcoholLevel > alcoholThreshold) {
    // Activate engine killswitch
    activateKillswitch();
  } else {
    // Deactivate engine killswitch
    deactivateKillswitch();
  }

  // Delay for stability
  delay(1000);
}

void activateKillswitch() {
  digitalWrite(motor1Pin, HIGH);
  digitalWrite(motor2Pin, LOW);
}

void deactivateKillswitch() {
  digitalWrite(motor1Pin, LOW);
  digitalWrite(motor2Pin, LOW);
}




```bash
# Install necessary libraries
arduino-cli lib install "MQUnifiedsensor"
