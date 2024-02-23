# iot-greenhouse-controller-pcb
A open source IoT enabled Greenhouse Controller board with a modular, extendable design

This project was born in the need of a way to provide an intelligent watering solution for plants with different water needs on a balcony while beinng on vacation. 
We had an autonomous but at the same time intelligent and connected system in mind that should have some advantages over the regular DIY "intelligent" watering systems you can find quite so often on the internet but also compared to some commercial, semi professional systems by some big brands that offer rather closed systems with not many truly intelligent features and little connectivity and extandability.

With this in mind we designed a modular set of boards to become what we call the IoT Greenhouse Controller.
It's core is based on an ESP32 S3 WROOM Module as main controller and for connectivity to the Internet via a local WiFi network. As a co-controller an ATMEGA32A MCU is used that communicates with the ESP32 via I2C (in Version 1 of the board) and via Serial (in Version 2 of the board).

The ESP32 side of the board offers an interface to an [OV2640](https://www.uctronics.com/download/cam_module/OV2640DS.pdf) (1600 x 1200 / UXGA  / 2 Megapixel) or [OV5640](https://cdn.sparkfun.com/datasheets/Sensors/LightImaging/OV5640_datasheet.pdf) (2592 x 1944 / QSXGA / 5 megapixel) camera module.

Multiple IOs for connection of Analog Soil Moisture sensors and digital output pins with MOSFETs are provided to connect to external sensors and actors.

# Current Status of the development
At this time the Version 1 of the board is in testing state. 
Version 2 is currently in Draft mode and first test PCBs are being produced.
We will shortly update the Schematics and Gerber files for Version 2.0 of the board.
The version 2 will focus on a 4 Layer PCB rather than the 2 layer PCB of Version one to reduce the size and with that also manufacturing costs.
We made the transition from 2 layer to 4 layer PCBs since most manufacturers nowadays produce 4 layer boards for almost the same price as 2 layer boards and the reduction in size of the overall board area, actually brings costs down.
Also we we went almost completely to SMD parts instead of usinng through hole parts, since many PCB manufacturers offer cheap part placement for standard components. This is not the most DIY friendly approach, but the size of the board would be to large if through hole components would be used throughout the project.

**At this state you can use all provided schematics and board designs at your own risk. The design might still contain bugs and we do not consider it as stable yet, until the first batches of the V2 Board have been produced.**

If the interest for "hand solderable" boards should be high, we might consider designing a separate PCB with mostly through hole components in the future.

# Prirmary Goals of the IoT Greenhouse Controller
- Modular approach to allow for easy exchange of components and upgrades without the need to replace the whole board for every improvement / iteration
- Easy extendibility to add addtional sensors and actors: measure moisture of the soil for each plant individually, mesarure temperature, humidty and light levels, control fans, lights and water pumps.
- truly connected IoT Device: connect to the controller with your browser, with an MQTT Broker, read weather data and log sensor data
- Individual water distribution for multiple plants: controlling multiple water outlets to deliver indidivual volumes of water to a large amounnt of different plants
- support connecting a camera module directly to allow taking fotos or streaming video of the plants/greenhouse via the IoT Greenhouse Controller directly
- Low cost components and full "hackability" by using of the shelf and popular Microcontrollers like the ESP32 and the ATMEGA

# Features of the IoT Greenhouse Controller Board
The IoT greenhouse controller board offers the following features:
- Support of a water flow sensor to measure dispensed water with an accuracy of a couple of ml
- Pump Control interface to control 12V water pumps or relais to control 120/240V pumps
- Camera Interface to connenct a low cost OV2640 or OV5640 camera module
- Plenty of 5V Analog Input pins (via Daisy-Chaining you can connect 8/16/24/32... sensors to the main unit) to connect low cost capacitve soil moisture sensors (e.g. https://amzn.eu/d/bsQ1Nxg)
- Plenty of digital output pins to control external components like LED light strings, solenoid water valves, fans etc.
- interfaces to control two low cost stepper motors (e.g. 28BYJ-48) with ULN2003 driver (4 pin stepper driver) (e.g. https://amzn.eu/d/im3X76l)
- relative light intensity sensor via an LDR (Light dependent resistor / Photoresistor) (e.g. https://amzn.eu/d/6Uyq5fR)
- interface for an Digital Temperature and Humidity Sensor like a DHT-21 or AM2301 Module (e.g. https://amzn.eu/d/2fSFoWb)
- interface for an MQ-135 Gas Sensor / Air Quality Sensor (e.g. https://amzn.eu/d/5kcbbQG)
- I2C interface pins for connecting external OLED (e.g. https://amzn.eu/d/0UacsuP) or LCD Displays or other I2C compatible devices
- a daisy-chainable solenoid valve and soil moisture sensor board to chain multiple water outlets and soil mosture sensor boards together, all controlled by a single main board
- usage of RS485 interface with low cost RJ12 Conectors for connecting the daisy-chaiend valve/sensor boards to the main unit with theoretical cable lengths of up to several hundred meters
- WiFi connectivity to allow controlling the IoT Greenhouse via the Internet and local WiFi Network
- Single supply voltage (12-24V) to provide all needed voltages for MCUs (3.3 and 5V), Camera, Sensors and Actors

