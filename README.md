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
## Week 8 homework:
### Walking Cat on a leash
#### Perspective View
![Breadboard](/week8/perspectiveView.JPG)
#### Front View
![Breadboard](/week8/frontView.JPG)
#### Side View
![Breadboard](/week8/sideView.JPG)
#### Bottom View
![Breadboard](/week8/bottomView.JPG)
### Walking Cat Side View
![Breadboard](/week8/sideWalk.gif)
### Walking Cat Front View
![Breadboard](/week8/frontWalk.mp4.gif)
## Week 9 homework:
### Walking Cat Unleashed
#### Perspective View
![Breadboard](/week9/walkingCatFinalPerspectiveView.JPG)
#### Front View
![Breadboard](/week9/walkingCatFinalFrontView.JPG)
#### Side View
![Breadboard](/week9/walkingCatFinalSideView.JPG)
#### Arduino H-Bridge Setup
![Breadboard](/week9/finalHBridgeArduinoSetUp.JPG)
### Walking Cat Unleashed Test Walk
![Breadboard](/week9/walkingCatUnleashed.gif)
### Walking Cat Unleashed VS Tanka
![Breadboard](/week9/walkingCatUnleashed2.gif)
## Week 10 Midterm:
### Walking Cat
### 3D Modeled Head in Blender
![Breadboard](/midterm/frontHeadModel.JPG)
![Breadboard](/midterm/sideHeadModel.JPG)
![Breadboard](/midterm/perspectiveHeadModel.JPG)
### Dancing Video
![Breadboard](/midterm/danceCat.gif)
### Schematic
![Breadboard](/midterm/walkingCatSketch2.jpg)
### Code
```cpp
  // This Code Makes Walking Cat Dance
const int toggleSwitch = 9; // Digital Pin 9 connects to the toggle switch
const int motorTerminal1 = 3; // Digital Pin 3 connects to motor terminal 1
const int motorTerminal2 = 2; // Digital Pin 4 connects to motor terminal 2
const int motorTerminal3 = 12; // Digital Pin 3 connects to motor terminal 1
const int motorTerminal4 = 13; // Digital Pin 4 connects to motor terminal 2
const int enablePin1 = 6; // Digital pin 9 connects to the enable pin
const int enablePin2 = 5; // Digital pin 9 connects to the enable pin

void setup() {

pinMode(toggleSwitch, INPUT); //the toggle switch functions as an input
pinMode(motorTerminal1, OUTPUT);
pinMode(motorTerminal2, OUTPUT);
pinMode(motorTerminal3, OUTPUT);
pinMode(motorTerminal4, OUTPUT);
pinMode(enablePin1, OUTPUT);
pinMode(enablePin1, OUTPUT);

digitalWrite(enablePin1, HIGH);
digitalWrite(enablePin2, HIGH);

}

void loop() {

if (digitalRead(toggleSwitch) == HIGH) {
forward();
delay(2000);
stand();
delay(500);
reverse();
delay(2000);
stand();
delay(500);
turn1();
delay(2000);
stand();
delay(500);
turn2();
delay(2000);
stand();
delay(500);
}
else {
stand();
}
}

void forward(){
digitalWrite(motorTerminal1, LOW); //forward direction
digitalWrite(motorTerminal2, HIGH);
digitalWrite(motorTerminal3, LOW); //forward direction
digitalWrite(motorTerminal4, HIGH);
}

void reverse(){
digitalWrite(motorTerminal1, HIGH); //reverse direction
digitalWrite(motorTerminal2, LOW);
digitalWrite(motorTerminal3, HIGH); //reverse direction
digitalWrite(motorTerminal4, LOW);
}

void stand(){
digitalWrite(motorTerminal1, LOW); // turns off motor
digitalWrite(motorTerminal2, LOW);
digitalWrite(motorTerminal3, LOW); // turns off motor
digitalWrite(motorTerminal4, LOW);
}

void turn1(){
digitalWrite(motorTerminal1, HIGH); //reverse direction
digitalWrite(motorTerminal2, LOW);
digitalWrite(motorTerminal3, LOW); //forward direction
digitalWrite(motorTerminal4, HIGH);
}

void turn2(){
digitalWrite(motorTerminal1, LOW); //forward direction
digitalWrite(motorTerminal2, HIGH);
digitalWrite(motorTerminal3, HIGH); //reverse direction
digitalWrite(motorTerminal4, LOW);
}
```
### YouTube Link "Making of Walking Cat"
### https://youtu.be/Up8T-Q4WoqU
### YouTube Link "Walking Cat Explained"
### https://youtu.be/JLUb9zZB5eY
## Week 11:
### Servo Motor Knob Arduino Example File
![Breadboard](/week11/servoKnob.mp4.gif)
![Breadboard](/week11/servoKnob.JPG)
![Breadboard](/week11/servoSchematicKnob.jpg)
### Code
```cpp
/*
 Controlling a servo position using a potentiometer (variable resistor)
 by Michal Rinott <http://people.interaction-ivrea.it/m.rinott>

 modified on 8 Nov 2013
 by Scott Fitzgerald
 http://www.arduino.cc/en/Tutorial/Knob
*/

#include <Servo.h>

Servo myservo;  // create servo object to control a servo

int potpin = 0;  // analog pin used to connect the potentiometer
int val;    // variable to read the value from the analog pin

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  val = analogRead(potpin);            // reads the value of the potentiometer (value between 0 and 1023)
  val = map(val, 0, 1023, 0, 180);     // scale it to use it with the servo (value between 0 and 180)
  myservo.write(val);                  // sets the servo position according to the scaled value
  delay(15);                           // waits for the servo to get there
```
### Servo Motor Sweep Arduino Example File
![Breadboard](/week11/servoSweep.mp4.gif)
![Breadboard](/week11/servoSchematicSweep.jpg)
### Code
```cpp
/* Sweep
 by BARRAGAN <http://barraganstudio.com>
 This example code is in the public domain.

 modified 8 Nov 2013
 by Scott Fitzgerald
 http://www.arduino.cc/en/Tutorial/Sweep
*/

#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  for (pos = 0; pos <= 180; pos += 1) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
  for (pos = 180; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
}
```
### Theremin with Photoresistor
![Breadboard](/week11/theremin.JPG)
![Breadboard](/week11/thereminSchematic.jpg)
### YouTube Link: https://www.youtube.com/watch?v=Ju3tf4kWSoI
### Code
```cpp

int sensorValue;
int sensorLow = 1023;
int sensorHigh = 0;

const int ledPin = 13;
void setup() {
  // put your setup code here, to run once:
  pinMode(ledPin, OUTPUT);
  digitalWrite(ledPin, HIGH);

  while (millis() < 5000){
    sensorValue = analogRead(A0);
    if (sensorValue > sensorHigh) {
      sensorHigh = sensorValue;
    }
    if (sensorValue < sensorLow) {
      sensorLow = sensorValue;
    }
  }
  digitalWrite(ledPin, LOW);

}

void loop() {
  // put your main code here, to run repeatedly:
  sensorValue = analogRead(A0);
  int pitch =
    map(sensorValue,sensorLow,sensorHigh,5,2000);
  
  tone(8,pitch,20);
  
  delay(10);

}
```
#### Credit to "Arduino Project Book"
![Breadboard](/week11/finalProjectProposal.jpg)
### Ideas:
#### I would like to focus on an interface to control a mechanical robot arm. I would like to use a combination of knobs and bottons to have manual and pre recorded functions. I would primarily forcus on the code and 3D printing the housing for all the eletronics to make it look like a professional product. If the servo motors arrive in time I will also make the arm itself, but will prototype with LEDs in the mean time.
### Link to robot arm example: https://www.youtube.com/watch?v=_B3gWd3A_SI
## Week 12:
### Servo Motor with Rotary Encoder
### Coded so that each step rotary encoder makes, the servo motor turns 1 degree
![Breadboard](/week12/slowServo.gif)
#### Code
```cpp
// This code enables a rotary encoder to control a servo motor
#include <Servo.h>

Servo myservo;

int encodeA = 5;
int encodeB = 6;

int counter = 90;
int aState;
int aLastState;

void setup() {
  pinMode (encodeA,INPUT);
  pinMode (encodeB,INPUT);

  Serial.begin (9600);

  aLastState = digitalRead(encodeA);
  myservo.attach(9);

}

void loop() {
  aState = digitalRead(encodeA);
  if (aState != aLastState){
    if (digitalRead(encodeB) != aState){
      counter ++;
    }
    else {
      counter --;
    }
    if (counter < 1){
    counter = 1;
  }
    if (counter > 178){
    counter = 178;
  }
    Serial.print("Position: ");
    Serial.println(counter);
  }

  myservo.write(counter);
  aLastState = aState;
}
```
### Coded so that each step rotary encoder makes, the servo motor turns 3.6 degrees degree
![Breadboard](/week12/fastServo.gif)
#### Code
```cpp
// This code controls a servo motor with a rotary encoder
//the code maps the vallue of the position of the rotary encoder to make the servo rotate more than value of the encoder for each step
#include <Servo.h>

Servo myservo;

int encodeA = 5;
int encodeB = 6;

int counter = 0; // gives a number value to the position of the rotary encoder
int counterMap; // a varriable to remap the value of the rotary encoder to 1-178 degrees
int aState;
int aLastState;

void setup() {
  pinMode (encodeA,INPUT);
  pinMode (encodeB,INPUT);

  Serial.begin (9600);

  aLastState = digitalRead(encodeA);
  myservo.attach(9);

}

void loop() {
  aState = digitalRead(encodeA);
  if (aState != aLastState){
    if (digitalRead(encodeB) != aState){
      counter ++;
    }
    else {
      counter --;
    }
    if (counter < 0){ //sets a min limit of 0
    counter = 0;
  }
    if (counter > 50){ //sets a max limit of 50
    counter = 50;
  }
    counterMap = map(counter, 0, 50, 1, 178); //maps the value of the encoder with the number of degrees a servo can turn
    Serial.print("Position: ");
    Serial.println(counter);
    Serial.println(counterMap);
  }

  myservo.write(counterMap); //turns the servo to the position value of the rotary encoder
  aLastState = aState;
}
```
### Schematic for both
![Breadboard](/week12/arduinoSchematic.JPG)
## Week 13:
### Servo Motor with Rotary Encoder and Botton 
### When the button is on the servo moves in smaller increments
![Breadboard](/week13/servoButtonMap.gif)
### Circuit
![Breadboard](/week13/servoButtonMap.JPG)
#### Code
```cpp
// This code enables a rotary encoder to control a servo motor
#include <Servo.h>

Servo myservo;

int encodeA = 8;
int encodeB = 9;
int toggle = 13;

int counter = 90;
int counterMap; // a varriable to remap the value of the rotary encoder to 1-178 degrees
int aState;
int aLastState;
int toggleState = 0;

void setup() {
  pinMode (encodeA,INPUT);
  pinMode (encodeB,INPUT);
  pinMode (toggle,INPUT);

  Serial.begin (9600);

  aLastState = digitalRead(encodeA);
  myservo.attach(10);


}

void loop() {
  toggleState = digitalRead(toggle);
  if(toggleState == HIGH){
  // fine control
  aState = digitalRead(encodeA);
  if (aState != aLastState){
    if (digitalRead(encodeB) != aState){      
      counter++;
    }
    else {
      counter--;
    }
    Serial.print("Position: ");
    Serial.print("ON: ");
    Serial.println(counter);
  }
  counterMap = counter;
  }
  else{ 
  // coarse control
  aState = digitalRead(encodeA);
  if (aState != aLastState){
    if (digitalRead(encodeB) != aState){
      counter = counter+5;
    }
    else {
      counter = counter-5;
    }
    Serial.print("Position: ");
    Serial.println(counter);
  }
  }
  counter = constrain(counter,0,180);
  myservo.write(counter);
  aLastState = aState;
}
```
## Final Project:
### Robot Arm 
#### This robot arm uses 3 servo motors and 3 rotary encoders to control the arms movements. It also has one button to have finer control of the movements. I used a 3D model file from howtomechatronics.com to create the arm. Their original design used 6 motors, but I modified the model to only use 3. I 3D printed all the parts in PLA plastic using the Ender 3 Pro.
### Testing all the movements
![Breadboard](/finalProject/jointTest.gif)
### Picking up an object
![Breadboard](/finalProject/pickUp.gif)
### Circuit and Arm Photo
![Breadboard](/finalProject/arm.JPG)
### Schematic
![Breadboard](/finalProject/finalArm.jpg)
### Code
```cpp

// This code controls a robot arm with 3 servo motors using rotary encoders. There is also a button that allows for fine control of the motor movements
#include <Servo.h>

Servo servoA;
Servo servoB;
Servo servoC;

// pins for the encoders and button
int encodeA = 2;
int encodeB = 3;
int encodeC = 5;
int encodeD = 6;
int encodeE = 8;
int encodeF = 9;
int toggle = 13;

// variables to track encoder movement and tell servo how many degrees to turn
int counterA = 90;
int aStateA;
int aLastStateA;
int counterB = 90;
int aStateB;
int aLastStateB;
int counterC = 90;
int aStateC;
int aLastStateC;
int toggleState = 0;

void setup() {
  pinMode (encodeA,INPUT);
  pinMode (encodeB,INPUT);
  pinMode (encodeC,INPUT);
  pinMode (encodeD,INPUT);
  pinMode (encodeE,INPUT);
  pinMode (encodeF,INPUT);
  pinMode (toggle,INPUT);

  Serial.begin (9600);

  aLastStateA = digitalRead(encodeA);
  servoA.attach(4);
  servoB.attach(7);
  servoC.attach(10);


}

void loop() {
  // see if the button is being pressed
  toggleState = digitalRead(toggle);
  if(toggleState == HIGH){
  // fine control when button is on
  servoHandFine();
  servoWristFine();
  servoArmFine();
  }
  else{ 
  // coarse control when botton is off
  servoHand();
  servoWrist();
  servoArm();
  }
  // make sure servo does not exceed minimum or maximum degrees
  counterA = constrain(counterA,0,180);
  counterB = constrain(counterB,0,180);
  counterC = constrain(counterC,0,180);
  // turn servo motors to the value of the encoder
  servoA.write(counterA);
  servoB.write(counterB);
  servoC.write(counterC);
  // record last state of encoder
  aLastStateA = aStateA;
  aLastStateB = aStateB;
  aLastStateC = aStateC;
}

// functions for all the servo motors
void servoHandFine(){
  aStateA = digitalRead(encodeA);
  if (aStateA != aLastStateA){
    if (digitalRead(encodeB) != aStateA){      
      counterA++;
    }
    else {
      counterA--;
    }
    Serial.print("Position: ");
    Serial.print("ON: ");
    Serial.println(counterA);
  }
}

void servoWristFine(){
  aStateB = digitalRead(encodeC);
  if (aStateB != aLastStateB){
    if (digitalRead(encodeD) != aStateB){      
      counterB++;
    }
    else {
      counterB--;
    }
    Serial.print("Position: ");
    Serial.print("ON: ");
    Serial.println(counterB);
  }
}

void servoArmFine(){
  aStateC = digitalRead(encodeE);
  if (aStateC != aLastStateC){
    if (digitalRead(encodeF) != aStateC){      
      counterC++;
    }
    else {
      counterC--;
    }
    Serial.print("Position: ");
    Serial.print("ON: ");
    Serial.println(counterC);
  }
}

void servoHand(){
  aStateA = digitalRead(encodeA);
  if (aStateA != aLastStateA){
    if (digitalRead(encodeB) != aStateA){
      counterA = counterA+5;
    }
    else {
      counterA = counterA-5;
    }
    Serial.print("Position: ");
    Serial.println(counterA);
  }
}

void servoWrist(){
  aStateB = digitalRead(encodeC);
  if (aStateB != aLastStateB){
    if (digitalRead(encodeD) != aStateB){
      counterB = counterB+5;
    }
    else {
      counterB = counterB-5;
    }
    Serial.print("Position: ");
    Serial.println(counterB);
  }
}

void servoArm(){
  aStateC = digitalRead(encodeE);
  if (aStateC != aLastStateC){
    if (digitalRead(encodeF) != aStateC){
      counterC = counterC+5;
    }
    else {
      counterC = counterC-5;
    }
    Serial.print("Position: ");
    Serial.println(counterC);
  }
}
```
