# floatinghyperspectralrobot
Problem Statement

Water bodies across India increasingly face contamination due to plastic waste, microplastics, suspended particles, and algal bloom events caused by rising chlorophyll concentration. Existing hyperspectral radiometers used for water quality assessment are expensive, bulky, and unsuitable for continuous field deployment or autonomous robotic monitoring.

The aim of this problem statement is to design and develop a low-cost, floating robotic platform capable of:

Performing multispectral reflectance measurements as an alternative to hyperspectral radiometers

Monitoring chlorophyll concentration indicators

Detecting plastic pollution and turbidity levels

Geotagging readings using GPS

Capturing surface images for visual confirmation

Transmitting all environmental data wirelessly through a LoRa communication module

The system must operate autonomously on water surfaces and provide real-time data suitable for environmental monitoring agencies or disaster management teams.

System Overview

The proposed system is an autonomous, floating robot capable of collecting multispectral, turbidity, optical, ultrasonic, GPS, and temperature data. The robot navigates water surfaces using a dual-motor propulsion system and periodically transmits sensor data packets over LoRa. A camera mounted on the robot captures images of the water surface for verification and mapping purposes.

The platform is designed to function as a low-cost replacement for traditional hyperspectral radiometers by using colour sensors, photodiodes, and turbidity sensors to approximate multispectral reflectance.

Hardware Components
Component	Purpose
Raspberry Pi 4B	Main controller, processing, LoRa, and camera handling
Pi Camera 1.3	Captures high-resolution images of water surface
TCS34725 Colour Sensor	Measures RGB reflectance for chlorophyll estimation
ADS1115 ADC	Reads analog turbidity and photodiode sensors
Turbidity Sensor	Detects particle density and plastic contamination
Photodiode Sensor	Measures optical intensity and reflectance patterns
HC-SR04 Ultrasonic Sensor	Detects obstacles
NEO-6M GPS	Provides latitude and longitude for readings
RFM95 LoRa Module	Long-range wireless data transmission
L298N Motor Driver	Controls two DC motors for movement
Dual DC Motors	Propulsion system for the robot
LEDs	Indicator signals
12V Battery	Power supply for motors and electronics
Software Features
Sensor Integration

The Raspberry Pi collects the following data in real time:

RGB colour reflectance

Turbidity

Photodiode intensity

Ultrasonic distance

Temperature (DS18B20)

GPS coordinates

Timestamped camera images

Motor Control

Two DC motors are driven using an L298N motor driver. The robot moves continuously at a set speed and can later be extended with obstacle avoidance or path-planning algorithms.

LoRa Transmission

Sensor readings are encoded as JSON and transmitted over LoRa using the RFM95 module. Data is received at a remote LoRa receiver for further processing or mapping.

Camera Capture

The Raspberry Pi Camera 1.3 captures images at regular intervals, stored locally for later analysis.

Data Packet Structure

A typical LoRa payload transmitted every cycle is:

{
  "timestamp": 1670000000.23,
  "temperature_c": 26.1,
  "colour": {...},
  "turbidity": {...},
  "photodiode": {...},
  "distance_cm": 45.2,
  "gps": {"lat": 12.9721, "lon": 80.2490}
}

How to Run the System

Enable necessary interfaces on Raspberry Pi:

I2C

SPI

Camera

Serial Port

1-Wire

Create a directory for camera images:

mkdir -p /home/abishek/captured


Run the program:

python3 finalcode.py

Applications

Monitoring chlorophyll concentration in lakes and reservoirs

Mapping plastic pollution zones

Early detection of algal blooms

Environmental research

Disaster response in flood-affected areas

Low-cost alternative to hyperspectral radiometry systems

Future Enhancements

Solar-powered autonomous operation

Full obstacle avoidance and path-planning

Real-time mapping dashboard

Deep learning-based plastic and debris detection

Multi-robot coordinated water monitoring
