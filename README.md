# IOT
https://wokwi.com/projects/333825443765420627
 https://wokwi.com/projects/333716279904961106
 https://wokwi.com/projects/334975793262232148
 https://wokwi.com/projects/334977496186356308

Working Principle of DHT11 Sensor

DHT11 sensor consists of a capacitive humidity sensing element and a thermistor for sensing temperature.  The humidity sensing capacitor has two electrodes with a moisture holding substrate as a dielectric between them. Change in the capacitance value occurs with the change in humidity levels. The IC measure, process this changed resistance values and change them into digital form.
For measuring temperature this sensor uses a Negative Temperature coefficient thermistor, which causes a decrease in its resistance value with increase in temperature. To get larger resistance value even for the smallest change in temperature, this sensor is usually made up of semiconductor ceramics or polymers.
The temperature range of DHT11 is from 0 to 50 degree Celsius with a 2-degree accuracy. Humidity range of this sensor is from 20 to 80% with 5% accuracy. The sampling rate of this sensor is 1Hz .i.e. it gives one reading for every second.  DHT11 is small in size with operating voltage from 3 to 5 volts. The maximum current used while measuring is 2.5mA.
 DHT11 Sensor


DHT11 sensor has four pins- VCC, GND, Data Pin and a not connected pin. A pull-up resistor of 5k to 10k ohms is provided for communication between sensor and micro-controller.

Pin diagram:
 
Code:
#include <dht.h>


#define dht_apin A0 // Analog Pin sensor is connected to
 
dht DHT;
 
void setup(){
 
  Serial.begin(9600);
  delay(500);//Delay to let system boot
  Serial.println("DHT11 Humidity & temperature Sensor\n\n");
  delay(1000);//Wait before accessing Sensor
 
}//end "setup()"
 
void loop(){
  //Start of Program 
 
    DHT.read11(dht_apin);
    
    Serial.print("Current humidity = ");
    Serial.print(DHT.humidity);
    Serial.print("%  ");
    Serial.print("temperature = ");
    Serial.print(DHT.temperature); 
    Serial.println("C  ");
    
    delay(5000);//Wait 5 seconds before accessing sensor again.
 
  //Fastest should be once every two seconds.
 
}// end loop(

Output:
 

Soil Moisture sensor
The soil moisture sensor is one kind of sensor used to gauge the volumetric content of water within the soil. As the straight gravimetric dimension of soil moisture needs eliminating, drying, as well as sample weighting. These sensors measure the volumetric water content not directly with the help of some other rules of soil like dielectric constant, electrical resistance, otherwise interaction with neutrons, and replacement of the moisture content.
Working Principle
This sensor mainly utilizes capacitance to gauge the water content of the soil (dielectric permittivity). The working of this sensor can be done by inserting this sensor into the earth and the status of the water content in the soil can be reported in the form of a percent.
This sensor makes it perfect to execute experiments within science courses like environmental science, agricultural science, biology, soil science, botany, and horticulture.
Specifications
The specification of this sensor includes the following.
•	The required voltage for working is 5V
•	The required current for working is <20mA
•	Type of interface is analog
•	The required working temperature of this sensor is 10°C~30°C

Soil Moisture Sensor Applications
The applications of moisture sensor include the following.
•	Agriculture
•	Landscape irrigation
•	Research
•	Simple sensors for gardeners
This is all about the soil moisture sensor. From the above information, finally, we can conclude that this sensor is used to gauge the soil’s volumetric water content, which makes it perfect to make experiments in the science field like agricultural science, soil science, horticulture, environmental science, biology, and botany.

Pin diagram
 
Code for analog mode
/*
	   Soil Moisture with Arduino - Analog Output
	   For more details, visit: https://techzeero.com/arduino-tutorials/soil-moisture-sensor-arduino/
	*/
	
	int sensorPin = A0;
	int outputValue ;
	
	void setup() 
	{
	   Serial.begin(9600);
	   Serial.println("Reading Data From the Sensor ...");
	   delay(2000);
	}
	
	void loop()
	{
	   outputValue= analogRead(sensorPin);
	   outputValue = map(outputValue,550,0,0,100);
	  
	   Serial.print("Moisture Value : ");
	   Serial.print(outputValue);
	   Serial.println("%");
	   delay(1000);
	}

 
Digital mode
/*
	   Soil Moisture with Arduino - Digital Output
	   For more details, visit: https://techzeero.com/arduino-tutorials/soil-moisture-sensor-arduino/
	*/
	
	int sensorPin = 7;
	int ledPin = 13;
	
	void setup() 
	{
	  pinMode(ledPin, OUTPUT);
	  pinMode(sensorPin, INPUT);
	  Serial.begin(9600);
	  Serial.println("Reading Data From the Sensor ...");
	  delay(2000);
	}
	
	void loop()
	{
	  if(digitalRead(sensorPin) == HIGH)
	  {
	    digitalWrite(ledPin, HIGH);
	  } 
	  else 
	  {
	    digitalWrite(ledPin, LOW);
	    delay(1000);
	  }
	}





Ultrasonic Sensor Working Principle
Ultrasonic sensors emit short, high-frequency sound pulses at regular intervals. These propagate in the air at the velocity of sound. If they strike an object, then they reflected back as an echo signal to the sensor, which itself computes the distance to the target based on the time-span between emitting the signal and receiving the echo.
 
Ultrasonic sensors are excellent at suppressing background interference. Virtually all materials which reflect sound can be detected, regardless of their colour. Even transparent materials or thin foils represent no problem for an ultrasonic sensor.
microsonic ultrasonic sensors are suitable for target distances from 20 mm to 10 m and as they measure the time of flight they can ascertain a measurement with pinpoint accuracy. Some of our sensors can even resolve the signal to an accuracy of 0.025 mm. Ultrasonic sensors can see through dust-laden air and ink mists. Even thin deposits on the sensor membrane do not impair its function.
Timing Diagram of Ultrasonic Sensor
 
1.	First, need to transmit trigger pulse of at least 10 us to the HC-SR04 Trig Pin.
2.	Then the HC-SR04 automatically sends Eight 40 kHz sound wave and wait for rising edge output at Echo pin.
3.	When the rising edge capture occurs at Echo pin, start the Timer and wait for a falling edge on Echo pin.
4.	As soon as the falling edge captures at the Echo pin, read the count of the Timer. This time count is the time required by the sensor to detect an object and return 
5.	back from an object
Pin diagram
 
Code
#define echoPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 3 //attach pin D3 Arduino to pin Trig of HC-SR04

// defines variables
long duration; // variable for the duration of sound wave travel
int distance; // variable for the distance measurement

void setup() {
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
  Serial.begin(9600); // // Serial Communication is starting with 9600 of baudrate speed
  Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
  Serial.println("with Arduino UNO R3");
}
void loop() {
  // Clears the trigPin condition
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
  // Displays the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
}

 



IR sensor


IR Sensor Working Principle
An infrared sensor includes two parts namely the emitter & the receiver (transmitter & receiver), so this is jointly called an optocoupler or a photo-coupler. Here, IR LED is used as an emitter whereas the IR photodiode is used as a receiver.
The photodiode used in this is very sensitive to the infrared light generated through an infrared LED. The resistance of photodiode & output voltage can be changed in proportion to the infrared light obtained. This is the fundamental IR sensor working principle.
The type of incident that occurred is the direct otherwise indirect type where indirect type, the arrangement of an infrared LED can be done ahead of a photodiode without obstacle. In indirect type, both the diodes are arranged side by side through a solid object ahead of the sensor. The generated light from the infrared LED strikes the solid surface & returns back toward the photodiode.
IR sensors use three basic Physics laws like Planck’s Radiation, Stephan Boltzmann & Wein’s Displacement.
•	Planck’s Radiation Law defines that the temperature of any object is not equivalent to Zero
•	Stephan Boltzmann Law defines that the whole energy which is generated at all wavelengths through a black body is associated with the total temperature.
•	Wein’s Displacement Law defines that the temperature of different objects emits spectra that are maximum at various wavelengths and inversely proportional with temperature.
IR Sensor Module
The IR sensor module includes five essential parts like IR Tx, Rx, Operational amplifier, trimmer pot (variable resistor) & output LED. The pin configuration of the IR sensor module is discussed below.
 
IR Sensor Module
•	VCC Pin is power supply input
•	GND Pin is power supply ground
•	OUT is an active-high o/p
The main specifications and features of the IR sensor module include the following.
•	The operating voltage is 5VDC
•	I/O pins – 3.3V & 5V
•	Mounting hole
•	The range is up to 20 centimeters
•	The supply current is 20mA
•	The range of sensing is adjustable
•	Fixed ambient light sensor

Pin diagram

 


Code:

const int ProxSensor=2;
int inputVal = 0;

void setup()
{
pinMode(13, OUTPUT);          // Pin 13 has an LED connected on most Arduino boards:
pinMode(ProxSensor,INPUT);    //Pin 2 is connected to the output of proximity sensor
Serial.begin(9600);
}

void loop()
{
if(digitalRead(ProxSensor)==HIGH)      //Check the sensor output
{
digitalWrite(13, HIGH);   // set the LED on
}
else
{
digitalWrite(13, LOW);    // set the LED off
}
inputVal = digitalRead(ProxSensor);
Serial.println(inputVal);
delay(1000);              // wait for a second
}

 
  


PIR sensor:

PIR Sensor’sWorking Principle
The PIR sensors are more complicated thanthe other sensors as they consists of two slots. These slots are made of a special material which is sensitive to IR. The Fresnel lens is used to see that the two slots of the PIR can see out past some distance. When the sensor is inactive, then the two slots sense the same amount of IR.The ambient amount radiates from the outdoors, walls or room,etc.
When a human body or any animal passes by, then it intercepts the first slot of the PIR sensor. This causes a positive differential change between the two bisects.When a human body leaves the sensing area,the sensor generates a negative differential change between the two bisects. The infrared sensor itself is housed in a hermetically sealed metal to improve humidity/temperature/noise/immunity. There is a window which is made of typically coated silicon material to protect the sensing element.
 PIR Sensor Working
A Motion Detection Circuit Using PIR Sensor
In the above segment, we have learned the pin outs of a PIR sensor, now let’s move on to study a simple application of the PIR sensor. The below diagram depicts a motion detector PIR sensor circuit. In the presence of a human IR energy or radiation, the infrared sensor detects the energy and immediately converts it into minute electrical pulses, enough to activate the transistor BC547 into conduction and to make its collector go low.
 Motion Detection Circuit Using PIR Sensor
As a comparator, the IC741 is set up –which consists of 8 pins. Wherein the pin3 is allocated as the reference input, while the Pin2 as the sensing input. When the collector terminal of the transistor goes low, then the potential pin2 of the IC becomes lower than the potential pin3. Immediately it makes the output of the IC high, triggering the relay driver consisting of another transistor and relay. The relay triggers and switches on the alarm device, which is connected to the circuit.
The capacitor 100uF/25V makes sure that the relay remains on even after the passive infrared sensor is turned off possibly due the exit of the radiation source. The PIR sensor device must be properly enclosed in a Fresnel lens cover to ensure that its efficiency is sufficiently enhanced.
PIR Sensor Based Projects with Abstracts
By understanding the use and limitations of sensors, gives a clear idea of developing the projects. Advanced level projects such as SCADA, fuzzy logic control, data acquisition usually adopts embedded systems and these projects requires software domain knowledge, especially the C language. Here, the details about a few passive infrared sensor based projects with description is given below.
PIR Sensor based Automatic Door Opening System
The main aim of this project is to opening and closing of doors,  in places wherein a person’s presence is mandatory – for instance, hotels, shopping malls, theaters,etc. this project consists of a PIR sensor that senses the presence of the human body and sends pulses to the 8051 microcontroller. This microcontroller controls the motor driver by sending suitable pulses to its input and enable pins.
Security Alarm System based on PIR sensor
The main intention of this project is to provide security. This project is based on PIR sensor with an integrated circuit which generates a siren. This sensor senses the infrared radiation which is emitted from the humans and then gives a digital output. This digital output is applied to the UM3561 IC. Thus, it generates the sound when any human body is detected. The UM3561 IC is a ROM IC, that generates multi siren tones such as fire engine sirens, ambulance sirens, machine gun sound and police sirens.
Human Detection Robot Using PIR Sensor
The human detection robot using PIR sensor mainly detects human, and it is based on an 8-bit microcontroller. A passive infrared sensors used to detect the human beings and this project is mainly used to rescue people stuck in debris during earthquake. It basically brings humans stuck under debris to the surface, thereby saving them effectively.
PIR Sensor based Stepper Motor Control
The main goal of this project is to control a stepper motor using PIR sensor. This project is mainly based on the robotic technology. This technology is mainly used for advanced applications. In this project, internally PIR sensor is used for excellent performance- IR sensor is used in burglar alarm systems, light switches, visitor present monitoring and robots. In robotics, stepper motors are used widely and they offer continuous rotation as well as amazing precision.
Thus, an overview of PIR sensor basics and its applications has been discussed. These sensors are used in many applications such as in real-time monitoring including physical  health, electronic security systems, etc. Apart from this, for any help regarding this topic or sensor based project ideas, you can contact us by commenting in the comment section below.
Photo Credits:
•	PIR Sensor Working by airlive
•	PIR Sensor by inmotion

Pin diagram
  
 
                     

Code:

int LED = 13;             // the pin that the LED is atteched to
int PIR = 2;              // the pin that the sensor is atteched to

void setup() {
  pinMode(LED, OUTPUT);   // initalize LED as an output
  pinMode(PIR, INPUT);    // initialize sensor as an input
  Serial.begin(9600);     // initialize serial
}

void loop(){
  if (digitalRead(PIR) == HIGH) { // check if the sensor is HIGH
    digitalWrite(LED, HIGH);      // turn LED ON 
    Serial.println("Motion detected!"); 
    delay(100);                   // delay 100 milliseconds 
  } 
  else {
    digitalWrite(LED, LOW);       // turn LED OFF
    Serial.println("Motion stopped!");
    delay(100);                   // delay 100 milliseconds
  }
}

 

https://wokwi.com/projects/333804541306733140

 
