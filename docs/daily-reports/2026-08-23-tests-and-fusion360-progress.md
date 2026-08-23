# Daily Project Report — 23 August 2026

## PX4–Jetson–GPS Autonomous Drone Project

### Daily Objective

The objective of today's work was to complete the remaining PX4 simulation tests and continue the mechanical design of the physical drone frame using Autodesk Fusion 360.

The work focused on two major areas:

1. PX4 GPS, telemetry, and failsafe testing.
2. Mechanical CAD design for the future physical drone.

---

# 1. PX4 Simulation Testing

## TEST-004 — GPS Position & Telemetry Monitoring

### Objective

Verify that the simulated drone can provide GPS position and telemetry information through PX4 and QGroundControl.

### Procedure

- Started the PX4 SITL simulation environment.
- Connected the simulated drone to QGroundControl.
- Verified GPS availability.
- Monitored the drone's position.
- Observed telemetry information during operation.
- Checked communication between PX4 and QGroundControl.
- Verified that flight and position information could be monitored correctly.

### Result

**PASS ✅**

GPS position and telemetry information were successfully monitored through QGroundControl.

### What I Learned

This test improved my understanding of:

- GPS position monitoring.
- Drone telemetry.
- PX4 and QGroundControl communication.
- Real-time flight information.
- The importance of telemetry for monitoring autonomous missions.

---

# 2. TEST-005 — Communication Failsafe & Safe Recovery

### Objective

Test how the PX4 system responds when the communication/telemetry connection with QGroundControl is interrupted.

### Procedure

- Started the PX4 simulation.
- Established communication with QGroundControl.
- Created a communication-loss condition.
- Observed the PX4 failsafe response.
- Monitored the drone's behavior during the failsafe condition.
- Verified safe system response and recovery.

### Result

**PASS ✅**

The system responded safely when communication was interrupted and demonstrated the expected failsafe behavior.

### What I Learned

This test improved my understanding of:

- Communication failsafe systems.
- Safety behavior in autonomous drones.
- PX4 failsafe configuration.
- The importance of backup behavior when communication is lost.
- Safe recovery procedures.

---

# 3. Simulation Testing Progress

The planned initial PX4 simulation test series has now been completed.

- TEST-001 — Takeoff, Hover & Return-to-Home ✅
- TEST-002 — GPS Waypoint Mission ✅
- TEST-003 — RTL Altitude & Safe Recovery ✅
- TEST-004 — GPS Position & Telemetry Monitoring ✅
- TEST-005 — Communication Failsafe & Safe Recovery ✅

### Simulation Test Status

**5 / 5 Tests Completed ✅**

This represents an important milestone in the project.

The project can now progress from initial simulation validation toward mechanical design, hardware integration, and eventually physical flight testing.

---

# 4. Fusion 360 Mechanical Design

After completing the simulation testing, work continued on the physical drone design using Autodesk Fusion 360.

### Drone Frame Development

The basic quadcopter frame was designed with:

- Four symmetrical drone arms.
- Central structural plate.
- Circular motor mounting areas.
- Motor mounting holes.
- Electronics mounting holes.
- Upper electronics platform.
- Structural standoffs.

The design was created with symmetry and future hardware integration in mind.

---

# 5. Main CAD Dimensions

The current design includes the following main dimensions:

- Main frame thickness: **3 mm**
- Motor mounting pad diameter: **30 mm**
- Motor center holes: **Ø3 mm**
- Central mounting holes: **Ø3 mm**
- Standoff outer diameter: **Ø8 mm**
- Standoff height: **10 mm**
- Upper electronics plate thickness: **2 mm**
- Upper electronics mounting plate: **90 × 110 mm**

---

# 6. Electronics Layout Planning

The drone frame was designed to support future integration of the main electronic systems.

These include:

- PX4/Pixhawk flight controller.
- NVIDIA Jetson companion computer.
- GPS and compass.
- Battery.
- Camera.
- Telemetry system.
- Power system.

Reference areas were created in Fusion 360 to study the physical space required by the electronics.

### Pixhawk

A reference footprint was created for the planned Pixhawk flight controller.

The current Pixhawk 6C reference footprint used in the CAD model is approximately:

**44 × 84.8 mm**

The flight controller is positioned close to the center of the drone to support good center-of-gravity and flight-control behavior.

### NVIDIA Jetson

A reference footprint was also created for the NVIDIA Jetson companion computer.

The current reference area is approximately:

**79 × 100 mm**

The Jetson will later provide additional computing capability for:

- Artificial intelligence.
- Computer vision.
- Object detection.
- Camera processing.
- Future autonomous navigation functions.

---

# 7. Electronics Mounting Platform

A second structural level was added above the main drone frame.

The current structure consists of:

**Main Drone Frame**

↓

**10 mm Standoffs**

↓

**Upper Electronics Mounting Plate**

The upper plate provides additional space for mounting the flight controller and companion computer while keeping the mechanical structure organized.

Four mounting locations were also added to the upper electronics plate.

---

# 8. Fusion 360 Skills Practiced

During today's CAD work, I practiced:

- Sketch creation.
- Center Rectangle.
- Center Diameter Circle.
- Sketch Dimension.
- Extrude.
- Join.
- Cut.
- Through All Cut.
- Center alignment.
- Symmetrical component placement.
- Standoff design.
- Electronics packaging.
- 3D model inspection.
- Mechanical layout planning.

---

# 9. Problems Encountered & Solutions

Several design challenges were encountered during the CAD process.

### Circle Alignment

Some mounting circles were initially positioned visually rather than using exact constraints.

The design was corrected by using:

- Exact dimensions.
- Center points.
- Symmetrical positioning.
- CAD constraints.

### Circular Pattern

Circular Pattern was initially tested for creating repeated mounting holes.

Manual dimension-controlled placement was later used where it provided easier verification and better control.

### Extrude Cut

Some hole profiles initially required adjustments before Fusion 360 recognized the correct body to cut.

The issue was resolved by checking:

- Extrusion direction.
- Selected profiles.
- Cut operation.
- Through All extent.

These problems were useful learning experiences and improved my understanding of CAD troubleshooting.

---

# 10. Current Project Result

Today's work completed two major project milestones.

### Software / Simulation

The initial PX4 simulation test roadmap reached:

**5 / 5 completed tests. ✅**

### Mechanical Design

The Fusion 360 drone frame progressed to the electronics integration stage.

The current CAD model includes:

- Main quadcopter structure.
- Four motor mounting areas.
- Motor mounting holes.
- Electronics mounting holes.
- Four structural standoffs.
- Upper electronics mounting platform.
- Pixhawk reference layout.
- Jetson reference layout.

The Fusion 360 project was saved as:

**PX4-Jetson-GPS-Drone-Frame-v1**

---

# 11. What I Learned Today

Today's work combined software testing and mechanical engineering design.

I improved my understanding of:

- PX4 flight simulation.
- GPS monitoring.
- Telemetry systems.
- Communication failsafes.
- Drone safety systems.
- Mechanical CAD design.
- Symmetrical frame design.
- Accurate dimensioning.
- Electronics packaging.
- Standoff-based mounting.
- Designing mechanical structures around electronic hardware.

This demonstrated how software, electronics, and mechanical engineering must work together when developing an autonomous drone.

---

# 12. Next Steps

The next phase of the project will continue the physical drone design.

Planned work includes:

1. Finalize NVIDIA Jetson mounting.
2. Design battery placement and retention.
3. Design GPS/compass mounting.
4. Finalize motor mounting geometry.
5. Plan cable and wire routing.
6. Review component clearances.
7. Review weight distribution.
8. Review center of gravity.
9. Improve frame geometry where necessary.
10. Perform final CAD inspection.
11. Prepare STEP/STL files for manufacturing or prototyping.
12. Prepare the physical hardware component list.
13. Begin physical drone assembly after design validation.

---

# Overall Daily Status

**TEST-004: PASS ✅**

**TEST-005: PASS ✅**

**PX4 Simulation Roadmap: 5/5 Completed ✅**

**Fusion 360 Frame Design: In Progress 🛠️**

**Next Major Task: Jetson Mounting & Hardware Layout**

---

## Project Goal

The long-term objective is to develop a GPS-enabled autonomous drone using PX4/Pixhawk and an NVIDIA Jetson companion computer.

The final system is intended to combine:

**Mechanical Design + PX4 Flight Control + GPS Navigation + Telemetry + Failsafe Systems + Computer Vision + AI + Autonomous Navigation**

This project is being developed as both an engineering learning project and a professional technical portfolio project.
