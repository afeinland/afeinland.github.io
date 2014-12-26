---
layout: post
title: "Remote Controlled Spinach Boat"
date: 2014-12-19 06:31:13
categories: blog post
---

###The Inception
![Empty spinach container](https://lh5.googleusercontent.com/1K11g3cf37TV-Uu3vNQS7RdFnvpIQMoi-EwrskOEwB4=w364-h591-no "Empty Spinach Container")

I eat a lot of spinach, so I go through a lot of these containers. I hate throwing them away (even if they are recycled), so one day I decided to save one and make something cool out of it.
Given the shape of the container, the obvious thing to make was a boat. I had a couple of XBee radios and a joystick sitting around, so I thought, why not make it remote controlled too? Thus, the RC spinach boat was born.

===

###The Craft
![Boat electronics](https://lh4.googleusercontent.com/DX9szNykL4OACJsJnIsKoTGMLK99s3qUNoWgYD3WZkg=w798-h247-no "Boat electronics")

The brains of the boat is an ATMega1284p which controls the servo (rudder), stepper motor (engine), and processes messages received from the controller via the XBee radio.
The stepper motor obviously isn't powerful enough to propel the boat, but I didn't want to buy a real motor. Four AA batteries power the craft.

===

###The Controller
![The controller](https://lh3.googleusercontent.com/TICtKi0RoXbWSVmTrfX-uiv-XLolkM8cHlHfDGqRm94=w1500-h290-no "The controller")

The controller consists of an ATMega328, a 2-axis joystick, and an XBee radio. The joystick is connected to the ATMega328's analog to digital converter, which calculates what position the joystick is in.
The X axis position on the joystick determines what position the servo should be in, and the Y axis position determines whether the motor should be on or off.
The servo position and motor on/off values are calculated locally from the output of the ADC and then sent to the craft via the XBee radio.

===

###The Final Product
![The completed boat](https://lh3.googleusercontent.com/Ptp9Gq-56Iix7ZvTqBSOobqdNBY-2and1tXyz2Jsvpo=w1188-h500-no "The completed Boat")

I mounted the servo and stepper motor into the boat and taped a rudder to the stern. It may not be the sexiest RC boat ever, but it works.

View the code [on Github](https://github.com/afeinland/dumboat "Spinach Boat Code")!



