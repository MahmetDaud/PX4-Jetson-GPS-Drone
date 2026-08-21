# System Requirements

## 1. Project Purpose

The purpose of this project is to design, simulate, build and test a GPS-assisted quadcopter using Pixhawk, PX4 and NVIDIA Jetson.

## 2. Project Budget

The preliminary target budget is USD 250–350. Final component selection will be based on safety, compatibility, availability and cost.

## 3. Drone Type

- Configuration: Quadcopter
- Frame: Four-arm frame
- Flight controller: Pixhawk
- Autopilot firmware: PX4
- Ground-control software: QGroundControl
- Companion computer: NVIDIA Jetson
- Navigation: GPS and compass

## 4. Core Functional Requirements

The drone shall be capable of:

- Stable manual flight
- GPS-assisted position hold
- Displaying its live GPS position
- Performing supervised waypoint missions
- Returning automatically to its home point
- Landing safely after a mission
- Communicating between Pixhawk and NVIDIA Jetson
- Sending telemetry data to the ground station

## 5. Preliminary Performance Targets

- Target flight time: 12–15 minutes
- Minimum GPS capability: Position hold and waypoint navigation
- Return-to-Home: Required
- Mission supervision: Required
- Flight testing: Simulation first, controlled outdoor testing later

These values are preliminary and may change after component selection and weight calculations.

## 6. Required Hardware

- Quadcopter frame
- Four brushless motors
- Four ESCs
- Pixhawk flight controller
- GPS and compass module
- NVIDIA Jetson
- Power module
- LiPo battery
- Propellers
- Radio transmitter and receiver
- Telemetry module
- Battery charger

## 7. Required Software

- PX4 Autopilot
- QGroundControl
- PX4 simulation environment
- NVIDIA JetPack
- Python
- MAVSDK
- MAVLink
- Fusion 360
- Git and GitHub

## 8. Safety Requirements

- Simulation must be completed before real flight
- Initial motor tests must be performed without propellers
- All sensors must be calibrated before flight
- Return-to-Home and failsafe settings must be configured
- Battery condition must be checked before every test
- Outdoor tests must be conducted in a safe and permitted area
- A pre-flight checklist must be completed before takeoff

## 9. Project Deliverables

- Working drone prototype
- Fusion 360 design files
- Source code
- Mission files
- Wiring documentation
- Build photographs
- Flight-test videos
- Test results
- Technical report
- GitHub repository documentation

## 10. Current Status

The repository and initial system requirements have been created. PX4 simulation setup is the next technical stage.
