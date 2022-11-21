# Experiment-no-7-DC-Motor-Speed-Control-Using-Arduino
### AIM : To control the speed and the direction of a DC motor using L293D driver ic( H- bridge)

### Components Required:
•	Arduino UNO board
•	L293D driver
•	12V DC motor
•	10K ohm potentiometer
•	Pushbutton
•	12V source
•	Breadboard
•	Jumper wires
### THEORY 
The L293D quadruple half-H drivers chip allows us to drive 2 motors in both directions, with two PWM outputs from the Arduino we can easily control the speed as well as the direction of rotation of one DC motor. (PWM: Pulse Width Modulation).
Arduino DC motor control circuit:
Project circuit schematic diagram is the one below.

![image](https://user-images.githubusercontent.com/36288975/167763051-b230c183-afc5-46f2-ba95-0f95e10dd6c9.png)
FIGURE-01 H BRIDGE CIRUCIT INTERFACE 
 
The speed of the DC motor (both directions) is controlled with the 10k potentiometer which is connected to analog channel 0 (A0) and the direction of rotation is controlled with the push button which is connected to pin 8 of the Arduino UNO board. If the button is pressed the motor will change its direction directly.
The L293D driver has 2 VCCs: VCC1 is +5V and VCC2 is +12V (same as motor nominal voltage). Pins IN1 and IN2 are the control pins where:
![image](https://user-images.githubusercontent.com/36288975/167763120-1421c2c5-8381-49eb-b376-03f6e1113b7a.png)
TABLE-01 EXITATION TABLE FOR H BRIDGE 

As shown in the circuit diagram we need only 3 Arduino terminal pins, pin 8 is for the push button which toggles the motor direction of rotation. Pins 9 and 10 are PWM signal outputs, at any time there is only 1 active PWM, this allows us to control the direction as well as the speed by varying the duty cycle of the PWM signal. The active PWM pin decides the motor direction of rotation (one at a time, the other output is logic 0).

### PRGORAM 
### Normal RPM:
```
const int motorpin1 = 5;
const int motorpin2 = 6;

void setup()
{
  pinMode(motorpin1, OUTPUT);
  pinMode(motorpin2, OUTPUT);
}

void loop()
{
  digitalWrite(motorpin1, HIGH);
  delay(2000);
  digitalWrite(motorpin2, LOW);
  delay(2000);
}
```
### To control RPM:
```
#define motorIn1 5
#define motorIn2 6

void setup()
{
  pinMode(motorIn1,OUTPUT);
  pinMode(motorIn2,OUTPUT);
}
void loop()
{
  clockwise(0);
  delay(3000);
  counterclockwise(50);
  delay(3000);
}
void counterclockwise(int speed)
{
  analogWrite(motorIn1,speed);
  analogWrite(motorIn2,0);
}

void clockwise(int speed)
{
  
  analogWrite(motorIn1,0);
  analogWrite(motorIn2,speed);
}
```
### OUTPUT
### CIRCUIT DIAGRAM:
![203054988-40df4bf0-7004-449b-857c-81c5a5cf7c0b](https://user-images.githubusercontent.com/94165377/203062897-bd10eb96-c680-4d37-9c95-5a819b981c94.png)
### READINGS:

### CLOCKWISE:

![203055078-a5cd1a88-1a48-4ee3-9c06-0eaa63e77d08](https://user-images.githubusercontent.com/94165377/203063146-e88fd8c5-b389-438a-9bdd-be0cffed4f82.png)
### Graph
![203055166-d0326989-fb6f-4af6-a0b5-c339de9f321f](https://user-images.githubusercontent.com/94165377/203063186-2f8a2088-93d4-4200-b586-1b798a29c4dd.png)
### COUNTER CLOCKWISE:

![203055192-8a25f4e8-6ee0-4bac-bf9d-c361cd88e659](https://user-images.githubusercontent.com/94165377/203063242-09120a11-a5ec-4b3d-9cab-c09d436fd203.png)
### Graph
![203055266-81edb58a-d997-4f03-be99-e6be14f05aeb](https://user-images.githubusercontent.com/94165377/203063274-7d271e0b-800a-4ca3-9e49-32499ab83e2b.png)



### RESULTS AND DISCUSSION 
Thus, the speed and the direction of a DC motor using L293D driver ic( H- bridge) is controlled.

