# 2020MechatronicsHomeWork
## Week 1 homework:
### Rhino
![Breadboard](/week1/rhino.JPG)
### Failed link
![Breadboard](/week1/failedLinks.JPG)
### Rhino motion
![Breadboard](/week1/rhino2.gif)
### Spider leg motion
![Breadboard](/week1/spider2.gif)
## Week 2 homework:
### Walking Cat
![Breadboard](/week2/walkingCat.JPG)
### Walking Cat motion
![Breadboard](/week2/walkingCatHandCrank.mp4.gif)
## Week 3 homework:
![Breadboard](/week3/motorCat.JPG)
![Breadboard](/week3/motorCat.mp4.gif)
## Week 4 homework:
### Arduino LDR controled LEDs
![Breadboard](/week4/ledControl2.gif)
### Arduino LDR controled LEDs circuit board
![Breadboard](/week4/ledControlSetUp.JPG)
### Arduino LDR controled LEDs code
```cpp
/*
  Program controls 3 LED lights based on a photoresistor's input value. the values are broken up into 4 tiers.
  The lower the tier value, the more LEDs light up. 

*/

// the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  //set pin 12,8 and 4 as outputs
  pinMode(12, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(4, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);
  delay(1);        // delay in between reads for stability
  // sets 4 conditions to determine how many LEDs will light up based on Photoresistor input value
  if (sensorValue >=650){
   digitalWrite(12, LOW);
   digitalWrite(8, LOW);
   digitalWrite(4, LOW);
  }
  if (sensorValue <=649){
      digitalWrite(12, HIGH);
      digitalWrite(8, LOW);
      digitalWrite(4, LOW);
  }
  if (sensorValue <=350){
   digitalWrite(12, HIGH);
   digitalWrite(8, HIGH);
   digitalWrite(4, LOW);
  }
    if (sensorValue <=275){
   digitalWrite(12, HIGH);
   digitalWrite(8, HIGH);
   digitalWrite(4, HIGH);
  }
}
```
## Week 5 homework:
### 3D Modeled walking cat in rhino
![Breadboard](/week5/walkingCatRhinoModel.JPG)
### Walking cat 3D printed parts and test fits
![Breadboard](/week5/walkingCat3dPrintParts.JPG)
### Arduino motor control with potentiometer and LED indicators video
#### GIF format makes top speed of motor look slower but it is really faster
![Breadboard](/week5/motorControlVideo.gif)
### Arduino motor control with potentiometer and LED indicators circuit board
![Breadboard](/week5/motorControlSetUp.JPG)
### Arduino motor control with potentiometer and LED indicators code
```cpp
/*
  This program controls the speed of a DC Motor using a potentiometer. 2 LED lights are used to indicate if
  The motor is recieving power. Green indicates power is on, Red indicates power is off. The DC motor needs
  an analog value of at least 75 to get the motor moving, thus the code is set up to stop giving power if
  the analog value is less than 75.

*/

// the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  //set pin 4,8 and 9 as outputs
  pinMode(4, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  //set pin A0 as input
  pinMode(A0, INPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // map the potentiometer value to be 0 to 255 to later control anologwrite values
  int outputValue = map(sensorValue, 0, 1024,0, 255);
  // print out the value you read:
  Serial.println(outputValue);
  delay(1);        // delay in between reads for stability
  // sets 2 conditions for how motor will recieve power
  // if the value is equal or less than 74 no power will be given to the motor and red LED will be on
  if (outputValue <=74){
   digitalWrite(9, LOW);
   digitalWrite(8, LOW);
   digitalWrite(4, HIGH);
  }
  // if the value is equal or greater than 75 power will be given to the motor based on the outputValue of the potentiometer
  // Green LED will be on
  if (outputValue >=75){
    analogWrite(9, outputValue);
    digitalWrite(8, HIGH);
    digitalWrite(4, LOW);
  }
}
```
## Week 6 homework:
### Continued 3D Modeled to determine 3D spacing
![Breadboard](/week6/walkingCat2.JPG)
### Arduino control motor with switch and H bridge
![Breadboard](/week6/motorOnAndOff.gif)
### Arduino control motor with switch and H bridge circuit board
![Breadboard](/week6/motorOnAndOff.JPG)
### Arduino control motor with switch and H bridge code
```cpp
  // This Code turns a motor on and off with a switch and uses a H bridge
const int toggleSwitch = 2; // Digital Pin 2 connects to the toggle switch
const int motorTerminal1 = 3; // Digital Pin 3 connects to motor terminal 1
const int motorTerminal2 = 4; // Digital Pin 4 connects to motor terminal 2
const int enablePin = 9; // Digital pin 9 connects to the enable pin
void setup() {
  // put your setup code here, to run once:
pinMode(toggleSwitch, INPUT); //the toggle switch functions as an input
pinMode(motorTerminal1, OUTPUT);
pinMode(motorTerminal2, OUTPUT);
pinMode(enablePin, OUTPUT);

digitalWrite(enablePin, HIGH);
}

void loop() {
  // put your main code here, to run repeatedly:
if (digitalRead(toggleSwitch) == HIGH) {
digitalWrite(motorTerminal1, LOW); //forward direction
digitalWrite(motorTerminal2, HIGH);
}
else {
digitalWrite(motorTerminal1, LOW); // turns off motor
digitalWrite(motorTerminal2, LOW);
}
}
```
## Week 7 homework:
### 3D Printed all Links and dowel attachment pieces
![Breadboard](/week7/3dPrintLinks.JPG)
### Created custom 3D printed motor to link addaptor piece
![Breadboard](/week7/motorAttached.JPG)
### Added cardboard support to keep motor in place
![Breadboard](/week7/cardboardSupport.JPG)
### Controled speed of walking links
#### Arduino code same as week5
![Breadboard](/week7/testLinkMotor.mp4.gif)
