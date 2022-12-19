# IxD256 Final Introduction
The inital concept is to further develop the last project by including visualization based on the weather data from the internet. The final outcome is mostly similar to the initial concept.
![alt text](https://github.com/Asimovq/IxD256Final/blob/main/1605225.png)

# Implementation
## Hardware
#### Resistor: 
For protecting the circuit.
#### M5Core-Ink: 
Controlling all the component in the circuit.
#### Relay: 
Control the humidifier based on the sensor data.
#### Photoresistor: 
Sensing the light intensity.
#### Humidifier: 
Generating Aroma.
![alt text](https://github.com/Asimovq/IxD256Final/blob/main/Adv_Prototyping_Project4_schem.png)

## Firmware

#### Input: 
Lighting density data from the Photoresistor
#### Output: 
The on/off state for the relay

```
#include "M5CoreInk.h"

const int ledPin = 10;  // built-in LED
const int sensorPin = 23;
int sensorValue = 0;
int brightnessVal = 0;
const int OutputPin = 32;
int noEmission = 0;
int currentState = noEmission;
int emission = 1;

#include <WiFi.h>
#include <AdafruitIO_WiFi.h>
#include "M5CoreInk.h"

// initialize WiFi connection:
// WiFiClient wifi;
// AdafruitIO_WiFi io(SECRET_AIO_USERNAME, SECRET_AIO_KEY, SECRET_SSID, SECRET_PASS);
// AdafruitIO_Feed *weatherfeed = io.feed("weatherfeed");
// AdafruitIO_Feed *ledFeed = io.feed("ledfeed");

unsigned long sensorTimer = 0;

void setup() {
  M5.begin();
  Serial.begin(9600);

  pinMode(ledPin, OUTPUT);
  pinMode(sensorPin, INPUT);

  // connect to io.adafruit.com
  Serial.print("Connecting to Adafruit IO");
  //io.connect();

  // set up a message handler for the ledFeed:
  //ledFeed->onMessage(handleMessage);

  // wait for a connection
  // while(io.status() < AIO_CONNECTED) {
  //   Serial.print(".");
  //   delay(500);
  // }

  //ledFeed->get();

  // print connection status
  //Serial.println(io.statusText());

  //M5.begin();
  pinMode(ledPin, OUTPUT);
  pinMode(OutputPin, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  // io.run(); is required for all sketches.
  // it should always be present at the top of your loop
  // function. it keeps the client connected to
  // io.adafruit.com, and processes any incoming data.
  //io.run();

  // read a 12-bit sensor value:
  int sensorVal = analogRead(sensorPin);

  // print sensorVal to Serial port:
  Serial.print("send sensorVal: ");
  Serial.println(sensorVal);

  // publish message every 5 seconds:
  if (millis() > sensorTimer + 5000) {
    sensorTimer = millis();
  }
}

//recieving

// void handleMessage(AdafruitIO_Data *data) {

//   Serial.print("received: ");
//   Serial.println(data->value());

//   if(strcmp((char*)data->value(), "ON")) {
//     digitalWrite(ledPin, HIGH);
//   }
//   else {
//     digitalWrite(ledPin, LOW);
//   }
// }
```

[Arduino Code Link](https://create.arduino.cc/editor/oskarqq/d3ecab0f-46c3-4f68-aff5-17ade2102290/preview)


## Software

## Integrations
Include a link to and/or screenshots of other functional components of your project, like Adafruit IO feeds, dashboards, IFTTT applets, etc. In general, think of your audience as someone new trying to learn how to make your project and make sure to cover anything helpful to explain the functional parts of it.

## Enclosure / Mechanical Design
Explain how you made the enclosure or any other physical or mechanical aspects of your project with photos, screenshots of relevant files such as laser-cut patterns, 3D models, etc. (it’s great if you’re willing to share the editable source files too!)



## Project outcome

Summarize the results of your final project implementation and include at least 2 photos of the prototype and a video walkthrough of the functioning demo.


## Conclusion
As you wrap up the project, reflect on your experience of creating it. Use this as an opportunity to mention any discoveries or challenges you came across along the way. If there is anything you would have done differently, or have a chance to continue the project development given more time or resources, it’s a good way to conclude this section.



## Project references
Please include links to any online resources like videos or tutorials that you may have found helpful in your process of implementing the prototype. If you used any substantial code from an online resource, make sure to credit the author(s) or sources.

