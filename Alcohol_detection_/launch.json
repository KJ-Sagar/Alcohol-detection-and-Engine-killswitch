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
