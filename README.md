# Automatic-Motion-Activated-Security-using-PIR-Sensor
## AIM:
     
To detect motion using a PIR sensor connected to an Arduino and trigger an LED (using the built-in LED) when motion is sensed.
             
## Hardware / Software Tools required:

1.	Arduino Uno R3 – 1 No
2.	PIR Sensor – 1 No
3.	LED (in-built on Arduino pin 13) – 1 No
4.	220-ohm resistor – 1 No (used with external LED if necessary)
5.	Breadboard – 1 No
6.	Jumper wires – As required
7.	USB Cable – 1 No (for uploading code and powering Arduino)
8.	Computer with Tinkercad or Arduino IDE installed

## Theory:
Passive Infrared (PIR) sensors are electronic devices that detect motion by sensing infrared radiation emitted by objects.Every object with a temperature above absolute zero emits infrared radiation. The PIR sensor detects this radiation and can sense motion when a warm object, such as a human body, passes within its detection range. The sensor contains a pair of pyroelectric sensors housed under a Fresnel lens, which focuses the infrared signals onto the sensor surface. When the infrared levels change rapidly between the two pyroelectric sensors—such as when a person walks by—the sensor outputs a HIGH signal indicating motion detection.PIR sensors are widely used in motion detection systems, security alarms, automatic lighting systems, and smart surveillance. They are popular due to their low power consumption, affordability, and ease of integration with microcontrollers such as the Arduino Uno. The sensor typically has three pins: VCC (power), GND (ground), and OUT (signal). When idle, the output pin remains LOW. Once motion is detected, the sensor sends a HIGH signal to the microcontroller, which can be used to trigger a response such as turning on an LED or activating an alarm.In this experiment, the PIR sensor is connected to an Arduino Uno board. The VCC pin of the sensor is connected to the 5V supply of the Arduino to power the sensor. The GND pin is connected to the Arduino’s ground. The OUT pin is connected to a digital input pin (pin 2 in this case) of the Arduino. The Arduino continuously monitors the state of the signal pin. If the signal pin goes HIGH, it means the sensor has detected motion, and the Arduino is programmed to turn ON the built-in LED on pin 13. If no motion is detected, the signal remains LOW, and the LED is turned OFF.

## Circuit Diagram:
<img width="1062" height="660" alt="image" src="https://github.com/user-attachments/assets/0b6bf651-068d-45b6-bcb0-7227cffee0e5" />

 
## Procedure: 

Step 1: Set Up the Tinkercad Environment

- Open Tinkercad in your browser and log in.

- Go to Circuits → click Create New Circuit to start a new project.

Step 2: Add Components to the Circuit

- Arduino Uno R3 – drag into the workspace.

- PIR Sensor – drag to the workspace.

 - Breadboard – add for LED and resistor connections.

 - LED – place on the breadboard.

 - Resistor (220Ω) – connect in series with the LED to limit current.

 - Buzzer – drag into the workspace for sound indication.

 - Jumper wires – use them to make all connections.

Step 3: Make the Connections

 - PIR Sensor → Arduino

 - VCC → 5V on Arduino

 - GND → GND on Arduino

 - OUT → Digital Pin 2 on Arduino

 - LED with Resistor → Arduino

 - Anode (+, long leg) → Digital Pin 13 on Arduino (via 220Ω resistor)

 - Cathode (–, short leg) → GND on Arduino

 - Buzzer → Arduino

 - Positive pin of buzzer → Digital Pin 12 on Arduino

 - Negative pin of buzzer → GND on Arduino

Step 4: Open the Code Editor

 - Click Code in Tinkercad.

 - Switch to Text Mode to prepare for writing the Arduino program.

Step 5: Simulate the Circuit

 - Click Start Simulation.

 - Move the virtual blue motion ball into the PIR sensor’s range.

 - The LED should turn ON.

 - The Buzzer should sound.

 - When no motion is detected:

 - The LED turns OFF.

 - The Buzzer stops.

Step 6: Troubleshoot and Refine

 - Double-check PIR sensor wiring (VCC–5V, GND–GND, OUT–D2).

 - Ensure LED polarity is correct (long leg → resistor → D13, short leg → GND).

 - Confirm buzzer polarity is correct (positive → D12, negative → GND).

 - Verify code is uploaded without errors.

Step 7: Save the Circuit

 - Click Stop Simulation after testing.

 - Save your project for future use.

# Code:
```
const int analogIn = A0;
int humiditysensorOutput = 0;
// Defining Variables
int RawValue= 0;
double Voltage = 0;
double tempC = 0;
double tempF = 0;
void setup(){
 Serial.begin(9600);
 pinMode(A1, INPUT);
}
void loop(){
 RawValue = analogRead(analogIn);
 Voltage = (RawValue / 1023.0) * 5000; // 5000 to get millivots.
 tempC = (Voltage-500) * 0.1; // 500 is the offset
 tempF = (tempC * 1.8) + 32; // convert to F
 Serial.print("Raw Value = " );
 Serial.print(RawValue);
 Serial.print("\t milli volts = ");
 Serial.print(Voltage,0); //
 Serial.print("\t Temperature in C = ");
 Serial.print(tempC,1);
 Serial.print("\t Temperature in F = ");
 Serial.println(tempF,1);
 humiditysensorOutput = analogRead(A1);
 Serial.print("Humidity: "); // Printing out Humidity Percentage
 Serial.print(map(humiditysensorOutput, 0, 1023, 10, 70));
 Serial.println("%");
 delay(5000); //iterate every 5 seconds
}
```


# Output:

https://github.com/user-attachments/assets/b4bacea7-5c40-4349-b48b-1aca6448c350


# Result:
The PIR sensor successfully detected motion and triggered the Arduino to turn ON the built-in LED. The LED remained OFF when no motion was present, confirming correct circuit and code functionality.

