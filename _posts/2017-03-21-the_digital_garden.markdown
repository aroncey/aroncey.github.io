---
layout: post
title:  "The Digital Garden"
date:   2017-03-21 17:56:36 +0000
---

RaspberryPi, Sensors, Python & Plants


VIsit the formatted version @ https://medium.com/@arthurroncey/the-digital-garden-bbadf064b6ff#.itu358mpp



For my second Flatiron blog post I discuss my past experience working with a single-board computer, the all powerful $35 RaspberryPi computer. I have had past experiences working with this platform but there are many others out there which offer various capabilities such as the Arduino.

A raspberryPi computer is a single-board computer created by the British RaspberryPi Foundation in the aim of promoting the teaching of basic computer science around the world and especially in developing countries.
“According to the Raspberry Pi Foundation, over 5 million Raspberry Pis have been sold before February 2015, making it the best-selling British computer.[7] By the 9th of September 2016 they had sold 10 million.[8]”
It has 4 usb inputs, a ethernet connection, HDMI, Wifi, Bluetooth, 40 Pins (26 GPIOs), Screen & camera peripherals and many more awesome tricks.
This computer can be used to create and manipulate electronic circuits which can be composed of hundreds of different sensors such as, UV captors, humidity levels, temperature reader, power switch tails, RFID, all types of motors etc…

https://jankarres.de/wp-content/uploads/2015/02/raspberry-pi-2-model-b.jpg
The computer can operate on different types of OS, like ubuntu or Windows IoT but the foundation now has an official OS call Raspbian, which is a Debian-based system designed by the RaspberryPi foundation.
“Debian is a Unix-like computer operating system that is composed entirely of free software, most of which is under the GNU General Public License” (link)
The GPIO pins are the most unique aspect of the computer, they allow the user to connect electric circuit components (sensors/or anything) to the computer and control that circuit with scripts {python, C, ruby, java, C++) allowing an infinite amount of possibilities.

and hundreds more ……
Here are some of the sensors that I have used:

This Soil Humidity Sensor is am analogue sensor that detects soil moisture level in soil (other are designed for liquids). It acts around a limit and produces two outputs: 0 or 1 in relationship to a limit that is set by the potentiometer on the sensor.
Paired with a Analogue/Digital converter chip (MCP3008) it can turn voltage readings to measurable data. Allowing the user to gather precise measurements % by the humidity sensor


Analogue/Digital converter MCP3008
Power Switch Tail is a simple component controlled by our code that allows you to control any sort of appliance that you would play into acting as an ON/OFF switch. I personally have UV lamps connected to a powerSwitch, providing the necessary lighting for my dear plants to survive in a NYC apartment.

Power Switch Tail connected to a raspberry Pi
Electric-Conductivity & PH Sensors — — These sensors would collect Ph & EC readings from the water containers in a hydroponic plant system. EC (electric-conductivity in this case is a measure of nutrients in the water; a higher EC reading would indicate that the water contains a lot of nutrients)

There are many more sensors that can be used with single-board computers to create any different types of circuits.

Python Scripts:
There are an infinite amount of possible combinations and rules that can be programmed to manage this type of system. I have personally coded in Python most of my scripts but any language can be used. Simple example below:

Power Switch Tail On/Off script
You access the GPIO pins by loading different types of Libraries, in a similar way that gems are loaded into a ruby program to access new functionalities.
Other example:

This is a basic python script that read the output of the GPIO pin connected to the humidity sensor and sends emails as a notification when there is a change to the humidity levels.

Playing around with Raspberry-Pi’s and similar platforms were some of the most formative experiences I had with computer programming before getting into web development. My short term goal is to improve my system and create proper interactive web applications to control all the components and allow me to host a dashboard on the raspberry-pi as a web-server.
Software development reside by nature most often in the realm of the digital world. Computers and projects like the Raspberry-Pi computer create a bridge that allows for an interaction between the physical world and the magic of the digital universe.


