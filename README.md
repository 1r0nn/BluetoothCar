# BluetoothCar
Made using Hardware and software. Toy car that connects to your smartphone.
- Implementation of C++ for remote control of a car via Bluetooth using a smartphone.
- Design and construction of the project from the ground up, involving components like Arduino and Microcontrollers.
- Integration of sensory features to mimic real-life car behaviors, including obstacle detection for a more authentic experience
- Components:
  - Argon
  - Breadboard
  - Car chassis
  - 2 x DC hobby motors
  - LiPo battery

## Images: 
<img width="489" alt="Screenshot_2023-08-19_at_12 30 01_PM_78" src="https://github.com/1r0nn/BluetoothCar/assets/112038371/5816ed77-2354-493e-817c-4d8b26de05a9">     ![Screenshot 2023-08-19 at 12 32 29 PM copy 2](https://github.com/1r0nn/BluetoothCar/assets/112038371/8851d403-8499-48fe-8545-746a5701c433)

## Source Code:

#include <SoftwareSerial.h>

SoftwareSerial SerialBT(10, 11); // RX, TX

int leftMotor = 9;
int rightMotor = 10;

void setup() {
  Serial.begin(9600);
  SerialBT.begin(9600);

  pinMode(leftMotor, OUTPUT);
  pinMode(rightMotor, OUTPUT);
}

void loop() {
  if (SerialBT.available()) {
    char data = SerialBT.read();

    switch (data) {
      case 'F':
        forward();
        break;
      case 'B':
        backward();
        break;
      case 'L':
        turnLeft();
        break;
      case 'R':
        turnRight();
        break;
    }
  }
}

void forward() {
  digitalWrite(leftMotor, HIGH);
  digitalWrite(rightMotor, HIGH);
}

void backward() {
  digitalWrite(leftMotor, LOW);
  digitalWrite(rightMotor, LOW);
}

void turnLeft() {
  digitalWrite(leftMotor, HIGH);
  digitalWrite(rightMotor, LOW);
}

void turnRight() {
  digitalWrite(leftMotor, LOW);
  digitalWrite(rightMotor, HIGH);
}

