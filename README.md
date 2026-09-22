# HealthGuard
# HealthGuard – Wearable Health and Environmental Monitoring System

## Overview

HealthGuard is an ESP32-based wearable monitoring prototype designed to monitor health, environmental, and motion-related parameters using multiple sensors. The system collects sensor data, processes it using the ESP32, and displays the information on a 128×64 OLED display. Sensor readings can also be viewed through the Serial Monitor for testing and development.

The project is designed as a modular platform that can be further developed into a compact wearable safety and health-monitoring device.

## Features

HealthGuard currently supports the following parameters:

* Temperature and humidity
* Heart rate
* SpO₂
* PM1.0, PM2.5, and PM10
* X, Y, and Z-axis acceleration
* X, Y, and Z-axis gyroscope data
* Basic health and environmental status detection

The OLED display switches between a Health page and an Environment page, allowing multiple parameters to be displayed using a single compact screen.

## Hardware Components

| Component     | Purpose                             |
| ------------- | ----------------------------------- |
| ESP32         | Main controller and data processing |
| DHT22(SHT31)        | Temperature and humidity            |
| MPU6050       | Acceleration and gyroscope          |
| MAX30102      | Heart rate and SpO₂ interface       |
| 128×64 OLED   | Data visualization                  |
| Potentiometer | PM2.5 simulation input              |

The system uses I²C communication for the OLED, MPU6050, and MAX30102 modules. The code defines the required I²C addresses and GPIO connections for the connected components.

## How It Works

When the system starts, the ESP32 initializes the connected sensors and OLED display. It also checks whether the MPU6050 and MAX30102 are available.

The DHT22 provides temperature and humidity readings. The MPU6050 provides acceleration and gyroscope data. The MAX30102 is detected by the system, but heart-rate and SpO₂ values are currently simulated for development and testing.

PM2.5 is currently simulated using a potentiometer. Its analog value is converted into a PM2.5 range, and corresponding PM1.0 and PM10 values are generated for testing.

The OLED alternates between two screens every second:

**Health Page**

* Temperature
* Humidity
* Heart rate
* SpO₂
* System status

**Environment Page**

* PM1.0
* PM2.5
* PM10
* System status

The same information, along with detailed motion data, is also printed to the Serial Monitor.

## Health Status

The system provides a simple `NORMAL` or `WARNING` status based on predefined conditions. A warning is generated when heart rate, SpO₂, temperature, or PM2.5 crosses the configured limits.

These thresholds are intended for prototype testing and should not be considered medical diagnostic limits.

## Current Status

The core sensor integration, OLED display, MPU6050 readings, DHT22 readings, status logic, and Serial Monitor output are implemented. Heart-rate, SpO₂, and particulate-matter readings are currently simulated.

## OUTPUT:
<img width="430" height="214" alt="Simulation Screenshot 1" src="https://github.com/user-attachments/assets/ad152b08-1e8c-4def-84e4-912921fe6a26" />

<img width="427" height="212" alt="Simulation Screenshot 2" src="https://github.com/user-attachments/assets/36ca2f2f-92bf-4fee-9bcc-4423967e4c04" />

## Future Development

Planned improvements include:

* Real MAX30102 heart-rate and SpO₂ processing
* Real PMS5003 particulate-matter integration
* Fall and abnormal-motion detection
* Emergency alerts and SOS functionality
* Wireless data transmission
* Data logging and remote monitoring
* Improved wearable hardware integration

## Project Goal

HealthGuard aims to provide a simple and scalable foundation for a wearable system that combines personal health monitoring, environmental awareness, and motion detection in a single device. The current prototype establishes the basic hardware and software architecture, which can be expanded with real sensor processing and additional safety features in future versions.
