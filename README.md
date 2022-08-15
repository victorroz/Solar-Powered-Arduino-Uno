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
    - [Assembling the solar powered battery charger](#assembling-the-solar-powered-battery-charger)
- [:clock2: Future ideas](#future-ideas)
- [:hand: How to contribute](#how-to-contribute)
    - [Manifest](#manifest)
- [:anchor: Materials](#materials)
- [:books: References](#references)
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

### Assembling the 555 timer circuit
In order to retain the charge of the battery as much as possible, a timer circuit was implemented. The main components of this circuit are a 555 timer IC and a 5V relay. Connection of individual components has been detailed in the following figure. The common terminal of the relay must be given the 5V output from the voltage booster to be activated. Since the voltage rating the relay is 5V, any supply lower than that will not switch it on.
![555 Timer Circuit Schema](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/41abd65237ab0b2d51489c88349c46d8fc291eee/images/555_Timer_Circuit_Schema.jpg)
![555 Timer Circuit Breadboard](https://github.com/victorroz/Solar-Powered-Arduino-Uno/blob/41abd65237ab0b2d51489c88349c46d8fc291eee/images/555_Timer_Circuit_Breadboard.jpg)

## Future ideas
- Make a PCB
- Use an OR gate IC instead of relays

## How to contribute
This is a free and open-source initiative. Anyone can make a contribution based on future ideas. If there are any suggestions that are not included in future ideas, they can be made. Also, if the future ideas presented are not applicable to this design and are not beneficial to the use case, one can make a proposal. If you want to help with development, you can look at the manifest of files listed below to get an understanding of what each file is about.

### Manifest
- /images - This is whre the image files for this README are
- /rawFiles - This contains all the raw or original source files from fritzing and draw.io
- /CITATION.cff - If anyone wants to use this repository as a reference then they can cite repository using the details provided this file 
- /README.md - This is the file you are currently reading!

## Materials
The materials required for this project are as follows:
<ol>
    <li>Arduino Uno [<a href="https://www.amazon.ca/ARDUINO-A000066-Uno-DIP-1-5/dp/B008GRTSV6/ref=sr_1_5?crid=1HO0GYEHUC4SL&keywords=arduino+uno&qid=1660604145&sprefix=arduino+uno%2Caps%2C135&sr=8-5">https://www.amazon.ca/ARDUINO-A000066-Uno-DIP-1-5/dp/B008GRTSV6/ref=sr_1_5?crid=1HO0GYEHUC4SL&keywords=arduino+uno&qid=1660604145&sprefix=arduino+uno%2Caps%2C135&sr=8-5</a>]</li>
    <li>Breadboard [<a href="https://www.amazon.ca/Breadboard-Solderless-Prototype-Distribution-Connecting/dp/B01EV6LJ7G/ref=pd_bxgy_img_sccl_2/131-0512123-6000825?pd_rd_w=iDQ8u&content-id=amzn1.sym.17b2b149-58e2-4824-ba79-851c5f351fdc&pf_rd_p=17b2b149-58e2-4824-ba79-851c5f351fdc&pf_rd_r=R3J504ECFW2WGFPBRRFN&pd_rd_wg=dokHs&pd_rd_r=5436eac7-824c-4fe0-a619-b27339f73f25&pd_rd_i=B01EV6LJ7G&psc=1">https://www.amazon.ca/Breadboard-Solderless-Prototype-Distribution-Connecting/dp/B01EV6LJ7G/ref=pd_bxgy_img_sccl_2/131-0512123-6000825?pd_rd_w=iDQ8u&content-id=amzn1.sym.17b2b149-58e2-4824-ba79-851c5f351fdc&pf_rd_p=17b2b149-58e2-4824-ba79-851c5f351fdc&pf_rd_r=R3J504ECFW2WGFPBRRFN&pd_rd_wg=dokHs&pd_rd_r=5436eac7-824c-4fe0-a619-b27339f73f25&pd_rd_i=B01EV6LJ7G&psc=1</a>]</li>
    <li>Jumper Wires [<a href="https://www.amazon.ca/Elegoo-120pcs-Multicolored-Breadboard-arduino/dp/B01EV70C78/ref=pd_day0fbt_img_sccl_1/131-0512123-6000825?pd_rd_w=7t2bc&content-id=amzn1.sym.8b6780d3-612a-41a1-b711-b85b62069095&pf_rd_p=8b6780d3-612a-41a1-b711-b85b62069095&pf_rd_r=Q6PMDMD2QHQERWVQAZAZ&pd_rd_wg=WyQ71&pd_rd_r=ada453ae-9118-4f62-9a2e-56708467c475&pd_rd_i=B01EV70C78&psc=1">https://www.amazon.ca/Elegoo-120pcs-Multicolored-Breadboard-arduino/dp/B01EV70C78/ref=pd_day0fbt_img_sccl_1/131-0512123-6000825?pd_rd_w=7t2bc&content-id=amzn1.sym.8b6780d3-612a-41a1-b711-b85b62069095&pf_rd_p=8b6780d3-612a-41a1-b711-b85b62069095&pf_rd_r=Q6PMDMD2QHQERWVQAZAZ&pd_rd_wg=WyQ71&pd_rd_r=ada453ae-9118-4f62-9a2e-56708467c475&pd_rd_i=B01EV70C78&psc=1</a>]</li>
    <li>5V step-up booster [<a href="https://www.amazon.ca/gp/product/B07KJVGVCM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07KJVGVCM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>TP4056 lithium battery charger [<a href="https://www.amazon.ca/gp/product/B083RTRJT6/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B083RTRJT6/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>6V Solar cell [<a href=https://www.amazon.ca/gp/product/B07BMMHMSJ/ref=ppx_od_dt_b_asin_image_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07BMMHMSJ/ref=ppx_od_dt_b_asin_image_s00?ie=UTF8&psc=1</a>]</li>
    <li>18650 lithium battery [<a href=""></a>]</li>
    <li>Battery holder [<a href="https://www.amazon.ca/gp/product/B08B86KHB2/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B08B86KHB2/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>1N4004 diode [<a href="https://www.amazon.ca/gp/product/B08KD73D81/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B08KD73D81/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>555 timer IC [<a href="https://www.amazon.ca/gp/product/B07RHKZ72L/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07RHKZ72L/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>2N3904 transistor [<a href="https://www.amazon.ca/gp/product/B07RTBJ1YZ/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07RTBJ1YZ/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>1MΩ resistor [<a href="https://www.amazon.ca/gp/product/B07JL6FGLM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07JL6FGLM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>100kΩ resistor [<a href="https://www.amazon.ca/gp/product/B07JL6FGLM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07JL6FGLM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>10kΩ resistor [<a href="https://www.amazon.ca/gp/product/B07JL6FGLM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B07JL6FGLM/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>100μF electrolytic capacitor [<a href="https://www.amazon.ca/gp/product/B089YDN6VJ/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B089YDN6VJ/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>10nF ceramic capacitor [<a href="https://www.amazon.ca/gp/product/B072J58YMT/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B072J58YMT/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
    <li>5V SPDT relay [<a href="https://www.amazon.ca/gp/product/B0874MF8DR/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1">https://www.amazon.ca/gp/product/B0874MF8DR/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1</a>]</li>
</ol>

## References
<ol>
    <li><a href="https://create.arduino.cc/projecthub/igorF2/solar-charged-battery-powered-arduino-uno-645d89?ref=platform&refid=424trendingpartintermediate&offset=5">Solar Charged Battery Powered Arduino Uno</a></li>
    <li><a href="https://create.arduino.cc/projecthub/eani/diy-how-to-use-the-arduino-uno-to-send-an-email-or-sms-28ac4d">DIY - How to Use the Arduino Uno to Send an Email or SMS</a></li>
    <li><a href="https://www.cbc.ca/news/canada/british-columbia/bc-wildfires-2021-timeline-1.6197751">A look back at the 2021 B.C. wildfire season</a></li>
    <li><a href="https://www.saskatchewan.ca/government/news-and-media/2022/august/11/spsa-reminds-residents-and-visitors-to-stay-cautious-to-prevent-wildfires">SPSA Reminds Residents and Visitors to Stay Cautious to Prevent Wildfires</a></li>
    <li><a href="https://en.wikipedia.org/wiki/Data_logger">Data logger</a></li>
</ol>