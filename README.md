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
## Week 4 homework:
![Breadboard](/week4/ledControlSetUp.JPG)
![Breadboard](/week4/ledControl2.gif)
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
  if (sensorValue >=131){
   digitalWrite(12, LOW);
   digitalWrite(8, LOW);
   digitalWrite(4, LOW);
  }
  if (sensorValue <=130){
      digitalWrite(12, HIGH);
      digitalWrite(12, HIGH);
      digitalWrite(4, LOW);
  }
  if (sensorValue <=25){
   digitalWrite(12, HIGH);
   digitalWrite(8, HIGH);
   digitalWrite(4, LOW);
  }
    if (sensorValue <=15){
   digitalWrite(12, HIGH);
   digitalWrite(8, HIGH);
   digitalWrite(4, HIGH);
  }
}
```
