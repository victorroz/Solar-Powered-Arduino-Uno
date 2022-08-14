# Solar Powered Arduino Uno

[![License: GPL v2](https://img.shields.io/badge/License-GPL_v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
![GitHub commit activity](https://img.shields.io/github/commit-activity/w/victorroz/Solar-Powered-Arduino-Uno?style=social)
[![Open Source Love svg2](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

## :package: About this project
One of the challenging task when designing a remote data logger is the power source. For instance, having an IoT (Internet of Things) device in a forest to detect forest fires where the mains power supply is not present. In such circumstances, the need for a standalone power supply, which has the means to generate electricity from the natural resources available to human, is ideal. A solar panel is used to charge up a battery which is then channeled through a voltage regulator to power up the Arduino and any other external components connected to it. A secondary battery has also been introduced to act as a backup power supply in case the primary one fails. This design project lays out a run-through of the modifications made to the already existing solar charged battery powered Arduino Uno.