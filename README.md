# Push Button, Temperature Sensors, Led

## Arduino made with TinkerCad

![Arduino](https://user-images.githubusercontent.com/82963539/154122238-1b3f68ca-082d-4006-9125-7384bda53413.png)

## General Description
When the push button is pressed,
the program reads the values of the 2 temperature sensors
and if the difference between them is more than 5,
then the led lights up.
## C++ code
```
//  C++ code   
// Author: Kitsios Marios, Date: 14/02/22

const int temp_pin1 = A0; // Temperature1
const int temp_pin2 = A3; // Temperature2

const int led = 2; // Led pin
const int push = 4; // Push 

int push_input;

void setup()
{
 pinMode(temp_pin1, INPUT);
 pinMode(temp_pin2, INPUT);
  
 pinMode(led,OUTPUT);

 pinMode(push,INPUT);
  
 Serial.begin(9600);
}

void loop()
{
  push_input = digitalRead(push);
  
  if (push_input == LOW){
    
    float temp_input1 = analogRead(temp_pin1);
    float temp_input2 = analogRead(temp_pin2);
    
    float temp1 = ( float(temp_input1) * 5 / 1023 ) * 100 - 50;
    float temp2 = ( float(temp_input2) * 5 / 1023 ) * 100 - 50;
    
    float cond1 = temp1 - temp2;
    float cond2 = temp2 - temp1;
    
    if ((cond1 >10) || (cond1 < -10)){
      digitalWrite(led,HIGH);
      delay(5000);
    }
    else if (cond2 >10 || cond2 <-10){
   	  digitalWrite(led,HIGH);
      delay(5000);
    }
    else {
      digitalWrite(led,LOW);
      delay(5000);
  	}  
  while (push_input == digitalRead(push)){}  
 }
}
```

## Schematic made with KiCad
![schematic_screenshot](https://user-images.githubusercontent.com/82963539/154504412-af43cebf-bc79-499b-a725-bdd5025e877e.jpg)

## PCB made with KiCad
![PCB_screenshot](https://user-images.githubusercontent.com/82963539/154506025-665f7095-fe67-41e1-a169-6d2e2a3ee886.jpg)

## Sample from KiCad's 3D Viewer
![image](https://user-images.githubusercontent.com/82963539/154508298-1e547f9a-882a-414d-ac3f-2a62c405de70.png)
