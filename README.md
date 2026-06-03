# Cereyan

Cereyan is a battery-powered smart ventilation fan platform designed for camping and tent airflow control.

The device is intended to attach magnetically to tent windows or fabric-supported openings and provide programmable ventilation through a compact embedded system. Multiple Cereyan units are planned to synchronize over ESP-NOW, allowing coordinated airflow control without requiring Wi-Fi infrastructure.

> Project status: Hardware design completed. PCB fabrication, board bring-up, firmware and mobile application development are planned as next steps.

## Motivation

Ventilation inside tents can be difficult to control, especially during camping, sleeping hours, humid conditions or hot weather. Cereyan is designed as a compact, battery-powered fan controller that can be mounted temporarily and programmed to run automatically.

The long-term goal is to create an open hardware and firmware platform for programmable off-grid ventilation.

## Planned Features

* Battery-powered operation
* USB-C charging input
* ESP32-C3-MINI based control system
* Power latch circuit for low-power wake/start behavior
* Programmable fan speed control
* Scheduled fan operation from a mobile application
* ESP-NOW synchronization between multiple units
* Battery voltage monitoring
* SK6812 addressable status LED
* Magnetic mounting concept for tent window usage

## Hardware Overview

The current hardware design includes:

* ESP32-C3-MINI microcontroller
* IP2312 battery charging circuit
* XB7608AJ battery protection IC
* Power latch circuit
* LDO-based system rail control
* MT3608 boost converter
* USB-C input
* SK6812 addressable RGB LED
* Battery voltage sensing
* Fan power/control interface

The power latch circuit allows the device to be started with a physical button. After startup, the ESP32-C3 takes control of the LDO enable pin to keep the system powered. This allows the firmware to manage shutdown behavior and reduce unnecessary battery drain.

## System Concept

A typical use case:

1. The user attaches one or more Cereyan fan units to tent windows using magnets.
2. Each unit powers up from its internal battery.
3. Units communicate with each other using ESP-NOW.
4. A mobile application is used to configure fan schedules and speed profiles.
5. The system automatically turns fans on/off or adjusts speed based on the programmed schedule.

Example planned commands:

* Turn fan on at a specific time
* Turn fan off at a specific time
* Set fan speed
* Read battery voltage
* Synchronize multiple units
* Apply the same schedule to a group of devices

## Current Status

Completed:

* PCB design
* Main hardware architecture
* Power latch concept
* Battery charging/protection section
* ESP32-C3 control section
* USB-C input section
* Boost converter section
* Status LED section

Pending:

* PCB manufacturing
* Board bring-up
* Electrical validation
* Firmware implementation
* ESP-NOW protocol design
* Mobile application
* Mechanical mounting validation
* Real-world camping tests

## Repository Structure

```text
hardware/      KiCad project files, schematic, PCB layout, BOM and manufacturing outputs
firmware/      ESP32-C3 firmware source code
mobile-app/    Mobile application source code
docs/          Design notes, bring-up checklist and roadmap
images/        Project images, renders and diagrams
```

## Roadmap

### Hardware Bring-up

* Verify power rails
* Test USB-C charging
* Validate battery protection behavior
* Test power latch operation
* Verify ESP32-C3 boot and programming
* Test battery voltage measurement
* Test fan output stage
* Test SK6812 LED

### Firmware

* Basic board support package
* Power management logic
* Fan speed control
* Battery voltage measurement
* LED status indication
* ESP-NOW communication
* Schedule execution logic
* Configuration storage

### Mobile Application

* Device discovery
* Fan speed control
* Schedule configuration
* Battery status display
* Multi-device grouping
* ESP-NOW gateway/configuration workflow

## Design Goals

* Practical off-grid usage
* Low standby power
* Simple charging through USB-C
* Field-programmable operation
* Multi-device synchronization
* Open and reproducible design
* Clear documentation for makers and embedded developers

## License

Hardware and software licensing will be finalized as the project progresses.

Suggested options:

* Hardware: CERN-OHL-S or CERN-OHL-P
* Firmware and mobile software: MIT License or Apache-2.0
