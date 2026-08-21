# Daily Progress Report — PX4 Jetson GPS Drone

## Report Information

| Item | Details |
|---|---|
| Project | PX4 Jetson GPS Drone |
| Report Type | Initial Setup and Simulation Progress Report |
| Work Period | 21–22 August 2026 |
| Author | Mohamed Daud Abdillahi |
| Department | Metallurgy and Materials Engineering |
| University | Karabük University |
| Project Status | Stage 1 — Planning and Simulation |
| Overall Result | Successful |

## 1. Project Overview

The PX4 Jetson GPS Drone project aims to design, simulate, build and test a GPS-assisted quadcopter based on the Pixhawk flight-controller platform, PX4 Autopilot and an NVIDIA Jetson companion computer.

The planned drone will eventually support GPS position monitoring, supervised waypoint missions, Return-to-Home, automatic landing and future intelligent-navigation functions.

The project is being developed in stages. Software simulation is being completed before hardware selection, assembly and real-flight testing.

## 2. Objectives of This Work Session

The objectives of the initial work session were to:

- Create a professional GitHub repository
- Define the project requirements
- Prepare a Windows-based PX4 development environment
- Install Ubuntu through WSL2
- Download and configure PX4 Autopilot
- Install the Gazebo simulator
- Build the PX4 SITL target
- Display the x500 quadcopter in Gazebo
- Install and connect QGroundControl
- Verify simulated GPS telemetry
- Conduct a controlled takeoff and hover test
- Conduct a Return-to-Home and automatic-landing test
- Document the results and problems encountered

## 3. GitHub Repository Setup

A public GitHub repository was created with the following name:

`PX4-Jetson-GPS-Drone`

The repository description identifies the project as an autonomous GPS navigation drone using Pixhawk, PX4 and NVIDIA Jetson.

The repository was initialized with:

- README file
- Python `.gitignore`
- MIT License
- Public visibility

### Files Created

| File | Purpose |
|---|---|
| `README.md` | General project overview, objectives and stages |
| `docs/system-requirements.md` | Preliminary technical and safety requirements |
| `test-results/test-001-takeoff-rth.md` | Formal documentation of the first flight test |
| `docs/progress-report-2026-08-22.md` | Daily project progress report |

## 4. Preliminary System Requirements

The project was defined as a quadcopter using:

- Pixhawk flight controller
- PX4 Autopilot
- GPS and compass module
- NVIDIA Jetson companion computer
- QGroundControl
- Four brushless motors
- Four electronic speed controllers
- LiPo battery and power module
- Radio-control and telemetry systems

The preliminary target budget was established as USD 250–350. Final component selection will be completed after compatibility, weight, power and safety calculations.

The preliminary target flight time is 12–15 minutes. These values may change after the final hardware configuration is selected.

## 5. Development Environment

### Host Computer

- Operating system: Windows 11
- Processor: 11th Generation Intel Core i5-11320H
- Installed memory: 8 GB RAM
- Primary drive: C Drive SSD
- Project storage: D Drive HDD

### WSL and Ubuntu

Windows Subsystem for Linux 2 was installed and configured. Ubuntu 22.04 was selected because it is supported by the PX4 development environment.

To protect the limited free space on the C Drive, Ubuntu was installed on the D Drive at:

`D:\WSL\Ubuntu-22.04`

A Linux user account named `mohamed` was created. The Ubuntu home directory was verified as:

`/home/mohamed`

Ubuntu packages were updated before the PX4 toolchain was installed.

## 6. PX4 Autopilot Setup

The official PX4 source code and its submodules were downloaded from GitHub using:

`git clone https://github.com/PX4/PX4-Autopilot.git --recursive`

The source code was stored at:

`/home/mohamed/PX4-Autopilot`

The official PX4 Ubuntu setup script was then executed:

`bash ./PX4-Autopilot/Tools/setup/ubuntu.sh`

This installed the required:

- PX4 build tools
- Gazebo Harmonic simulator
- C and C++ development packages
- Python dependencies
- Pixhawk firmware toolchain
- Simulation libraries and plugins

## 7. PX4 SITL and Gazebo Simulation

The initial simulation used:

- PX4 Software-in-the-Loop
- Gazebo Harmonic
- x500 quadcopter model

The original simulation command was:

`make px4_sitl gz_x500`

The PX4 build completed after resolving a memory-related problem. Gazebo then launched and created the `x500_0` simulated vehicle.

The successful working command was:

`LIBGL_ALWAYS_SOFTWARE=1 make -j1 px4_sitl gz_x500`

## 8. Problems Encountered and Solutions

### 8.1 Insufficient RAM During Compilation

#### Problem

The first build stopped during C++ compilation and displayed:

`fatal error: Killed signal terminated program cc1plus`

Task Manager showed:

- High memory usage
- D Drive at 100% activity
- Active CPU utilisation

The compiler process was terminated because the 8 GB system memory was nearly exhausted.

#### Solution

The build was restarted with only one compilation job:

`make -j1 px4_sitl gz_x500`

The `-j1` option reduced memory usage by allowing only one major compilation operation at a time. The build was slower but completed successfully.

### 8.2 Slow Initial Build

#### Problem

The PX4 build appeared to remain at one step for a long time.

#### Cause

The Ubuntu installation and PX4 source code were stored on the D Drive, which is an HDD. Linking large Gazebo libraries required significant disk activity.

#### Solution

System performance was monitored through Task Manager. The build was allowed to continue while CPU and disk activity confirmed that it was still working.

### 8.3 Gazebo Grey Display

#### Problem

Gazebo launched, but the simulation window remained grey and the x500 vehicle was not rendered visibly.

#### Solution

Gazebo was restarted with software rendering:

`LIBGL_ALWAYS_SOFTWARE=1 make -j1 px4_sitl gz_x500`

The x500 quadcopter then appeared correctly in the simulation.

### 8.4 QGroundControl Did Not Connect Automatically

#### Problem

QGroundControl for Windows displayed:

`Disconnected — Click to manually connect`

#### Solution

The WSL IP address was obtained using:

`ip addr | grep eth0`

The detected WSL IP address during the session was:

`172.18.68.48`

A manual UDP communication link was created in QGroundControl with:

- Link name: PX4 WSL Simulation
- Type: UDP
- Server address: `172.18.68.48`
- Port: `18570`

QGroundControl then connected successfully to PX4 SITL.

The WSL IP address is dynamic and may change after WSL or Windows restarts. It must be checked again before future Windows QGroundControl connections.

## 9. QGroundControl Configuration

QGroundControl Daily was installed on Windows 11.

The initial preferences were configured as follows:

| Setting | Selection |
|---|---|
| Preferred firmware | PX4 Pro |
| Preferred vehicle | Multi-Rotor |
| Units | Metric System |
| Horizontal distance | Metres |
| Vertical distance | Metres |
| Speed | Metres per second |
| Temperature | Celsius |

After establishing the UDP connection, QGroundControl displayed:

- Vehicle status: Ready
- Flight mode: Hold
- GPS satellite count: 10
- Simulated battery level: 100%
- Vehicle position on the map
- Altitude and speed telemetry

## 10. First Simulated Flight Test

The first simulated flight test included:

1. Establishing the PX4 and QGroundControl connection
2. Confirming vehicle-ready status
3. Confirming GPS availability
4. Selecting a 3-metre commanded takeoff height
5. Arming the x500 quadcopter
6. Executing vertical takeoff
7. Observing a stable hover
8. Activating Return-to-Home
9. Observing automatic landing
10. Confirming automatic disarming

### Test Results

| Parameter | Result |
|---|---|
| GPS satellites | 10 |
| Commanded takeoff height | 3 m |
| RTL height reported by PX4 | 4 m |
| Stable hover | Successful |
| Return-to-Home | Successful |
| Automatic landing | Successful |
| Automatic disarming | Successful |
| Final altitude | 0.0 m |
| Final horizontal speed | 0.0 m/s |
| Final vertical speed | 0.0 m/s |
| Flight duration | 2 minutes 31 seconds |
| Overall result | PASS |

### PX4 Terminal Evidence

PX4 reported the following events:

- `Ready for takeoff!`
- `Armed by external command`
- `Takeoff detected`
- `RTL: start return at 4 m`
- `RTL: land at destination`
- `Landing detected`
- `Disarmed by landing`

A PX4 `.ulg` flight-log file was generated automatically.

## 11. Skills and Knowledge Developed

During this work session, practical experience was gained in:

- GitHub repository creation
- Technical Markdown documentation
- Windows Subsystem for Linux
- Ubuntu command-line operations
- Git and source-code cloning
- PX4 development-environment setup
- Software-in-the-Loop simulation
- Gazebo vehicle simulation
- QGroundControl installation and configuration
- MAVLink UDP communication
- WSL networking
- GPS telemetry monitoring
- Takeoff and hover operations
- Return-to-Home testing
- Technical troubleshooting
- Test-result documentation

## 12. Current Project Status

Stage 1 has successfully started. The development environment is operational, and the first simulated flight test has passed.

### Completed

- GitHub repository
- Project README
- System-requirements document
- WSL2 and Ubuntu installation
- PX4 Autopilot setup
- Gazebo simulation setup
- QGroundControl setup
- GPS position display
- Takeoff and hover test
- Return-to-Home test
- Automatic landing
- TEST-001 documentation

### Not Yet Completed

- Supervised waypoint mission
- Additional simulation tests
- Hardware component selection
- Fusion 360 frame design
- Physical drone assembly
- Pixhawk hardware configuration
- NVIDIA Jetson integration
- Camera and computer vision
- Real outdoor flight testing

## 13. Next Planned Work

The next activity is:

**TEST-002 — Supervised GPS Waypoint Mission**

The planned test will include:

- Starting the x500 simulation
- Reconnecting QGroundControl
- Opening Plan View
- Creating three or four GPS waypoints
- Setting safe simulated altitudes
- Uploading the mission to PX4
- Starting the mission under supervision
- Monitoring waypoint completion
- Activating Return-to-Home
- Documenting results and screenshots

## 14. Conclusion

The initial PX4 Jetson GPS Drone project setup was successful. The software environment was prepared, the simulated x500 quadcopter was created, and QGroundControl was connected through MAVLink over UDP.

The vehicle successfully completed takeoff, stable hover, Return-to-Home, automatic landing and disarming. The problems involving limited RAM, slow HDD performance, Gazebo rendering and WSL network communication were identified and resolved.

The project is ready to continue with supervised GPS waypoint testing before progressing to hardware design and physical construction.
