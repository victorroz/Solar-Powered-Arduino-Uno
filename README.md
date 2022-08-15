# Solar Powered Arduino Uno

[![License: GPL v2](https://img.shields.io/badge/License-GPL_v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
![GitHub commit activity](https://img.shields.io/github/commit-activity/w/victorroz/Solar-Powered-Arduino-Uno?style=social)
[![Open Source Love svg2](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

## Table of Contents
- [:package: About this project](#about-this-project) 
- [:coffee: Overview](#overview)
    - [Introduction](#introduction)
    - [Why?](#why)
    - [Objective](#objective)
    - [Issue](#issue)
- [:art: The design](#the-design)
    - [Details](#details)

## About this project
![Solar Powered Arduino Uno Banner](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/main/images/Banner.png)
*One of the challenging task when designing a remote data logger is the power source. For instance, having an IoT (Internet of Things) device in a forest to detect forest fires where the mains power supply is not present. In such circumstances, the need for a standalone power supply, which has the means to generate electricity from the natural resources available to human, is ideal. A solar panel is used to charge up a battery which is then channeled through a voltage regulator to power up the Arduino and any other external components connected to it. A secondary battery has also been introduced to act as a backup power supply in case the primary one fails. This design project lays out a run-through of the modifications made to the already existing solar charged battery powered Arduino Uno.*

## Overview
### Introduction
The Arduino Uno is an open-source microcontroller board based on the ATmega328P microchip microcontroller. The board is developed by Arduino.cc which comes with an arrangement of digital and analog input/output (I/O) pins. The I/O pins can be used to provide power and control external components, and can also be interfaced with other expansion shields. As a result, sensors, such as temperature and humidity, could be wired with the Arduino to make a standalone system. One such example of standalone systems is referred to as data loggers. To explain it further, a Wikipedia article [5] states that data loggers are electronic devices that collect information over time by using sensors. This led to the main objective of this project which is to make use of nature energy, given its abundance and pure in form, to power up devices in remote locations. The search for renewable energy sources is a continuous process and the discovery of solar energy gave rise to numerous possibilities. One of them is an alternative source of power where a power outlet is not available. This project makes use of a 6V solar cell that charges up a 3.7V lithium battery. A voltage booster is then used to step-up the voltage to 5V, which can then be used to power the Arduino board and other components connected to it. In order to reserve battery energy, a timer circuit was also implemented to momentarily cut-off the power from the Arduino. Additionally, a secondary battery has been introduced to assist the primary battery in case it malfunctions and stops supplying power to the microcontroller.

![Solar Battery Charger Block Diagram](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/cd2b4fa262351bdbf0899aed054e404ec7fb3325/images/Solar_Battery_Charger_Block_Diagram.jpg)
![555 Timer Circuit Block Diagram](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/cd2b4fa262351bdbf0899aed054e404ec7fb3325/images/555_Timer_Circuit_Block_Diagram.jpg)

### Why?
In 2021, the province of British Columbia in Canada experienced some of the most terrifying forest fires recorded in history [3]. Furthermore, in the midst of writing this report, the Government of Saskatchewan has declared seven active wildfires in the province as of 11 August 2022 [4]. Even though there are satellites working around the clock to detect such disasters, having locally placed data loggers may result in faster information relays. However, the problem arises when the supply of electricity comes into question. Every man-made device requires some kind of electrical charge to start functioning. As such, the remote data logger also needs a power source to begin collecting data. The issue is that the device will be placed in a remote location, such as a forest, where there is no presence of power outlets. To overcome this, making use of solar energy is a feasible option. Furthermore, as mentioned previously, a secondary battery will also be added which will support the primary battery when it fails to supply power to the system.

### Objective
The primary objective of this project is to design a system that will be able to power an Arduino board using solar energy. With the progress of IoT devices being made for various purposes, especially for use in forests to detect forest fires and gather environment conditions, this system will encourage developers to make better devices without getting worked up on the source of power supply. Before proceeding with the project, a reference was taken from the already existing project done by Igor Fonseca Albuquerque on Arduino Project Hub [1]. 

### Issue
The major issue with this reference project was finding the exact components required to make the solar charger and timer circuit. As the author published this in the year 2016, some of the components were discontinued or out of stock. As a result, quite a bit of additional time was spent finding out the right components. In addition to the already incredible circuit made by Igor, a few modifications were done to it. Since the architecture was only using one lithium battery, a failure in the power source would have left the Arduino in an offline state. To overcome this issue, a secondary battery was introduced to serve as an emergency reserve.

## The design
### Details
The main driving mechanism for this project is the solar panel, as it will be used to power up the Arduino. As mentioned previously, there will be two parts to this system design. The first part consists of two of the charging circuits (one for primary and the other for secondary battery) and the second part consists of the timer circuit. Fritzing, an open- source CAD software, has been used to implement the circuit before soldering. 
### Assembling the solar powered battery charger
As portrayed in the schematic view, the positive output of the solar panel is connected to the 1N4004 diode which is then connected to the positive terminal of the battery charger. The 3.7V 18650 lithium battery is connected in a junction between the battery charger and the voltage booster. The battery gets charged and then stepped up to a 5V output. This 5V output is the required voltage to power the Arduino. It is to be noted that, the battery and voltage booster used in the simulation software does not match with the one that has been used in this project. At this point, the Arduino can already be turned on but the battery will be drained quickly.
![Solar Battery Charger Schema](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/41abd65237ab0b2d51489c88349c46d8fc291eee/images/Solar_Battery_Charger_Schema.jpg)
![Solar Battery Charger Breadboard](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/41abd65237ab0b2d51489c88349c46d8fc291eee/images/Solar_Battery_Charger_Breadboard.jpg)
