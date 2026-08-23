# TEST-005 — GCS Connection Loss Failsafe and Safe Recovery

## Test Summary

| Item | Result |
|---|---|
| Test ID | TEST-005 |
| Environment | PX4 Software-in-the-Loop (SITL) |
| Vehicle | Gazebo x500 Quadcopter |
| Ground Station | QGroundControl Daily |
| Test Result | **PASS** |

## Objective

The objective of this test was to verify that the PX4 simulated x500 quadcopter could respond safely to the loss of the Ground Control Station connection.

The test focused on:

- Detecting loss of QGroundControl connection
- Activating the PX4 failsafe
- Entering a temporary Hold state
- Starting Return-to-Launch (RTL)
- Returning toward the home position
- Landing automatically
- Disarming safely after landing

## Test Configuration

- Operating System: Windows 11
- Linux Environment: Ubuntu 22.04 on WSL2
- Autopilot: PX4 SITL
- Simulator: Gazebo Harmonic
- Vehicle Model: x500 Quadcopter
- Ground Control Station: QGroundControl Daily
- Communication: MAVLink over UDP

## Test Procedure

1. Started PX4 SITL with the Gazebo x500 vehicle.
2. Connected QGroundControl to the simulated vehicle.
3. Confirmed that the vehicle was Ready and GPS was available.
4. Commanded the vehicle to take off to approximately 3 metres.
5. Maintained the vehicle in Hold mode.
6. Closed QGroundControl while the vehicle was airborne.
7. Observed PX4 detecting the loss of the Ground Control Station connection.
8. Observed the failsafe entering Hold for 5 seconds.
9. Confirmed failsafe activation.
10. Confirmed that PX4 initiated Return-to-Launch.
11. Observed automatic landing.
12. Confirmed that the vehicle disarmed after landing.

## Observed PX4 Failsafe Sequence

The PX4 terminal displayed the following sequence:

- Connection to ground station lost
- Failsafe activated: entering Hold for 5 seconds
- Failsafe activated
- RTL: start return at 4 m
- RTL: land at destination
- Landing detected
- Disarmed by landing

## Results

The test was completed successfully.

The simulated PX4 x500 quadcopter detected the loss of the Ground Control Station connection and initiated the configured failsafe response.

The vehicle first entered Hold mode for approximately 5 seconds, then initiated Return-to-Launch, landed automatically and safely disarmed.

## Flight Evidence

Evidence captured during TEST-005 includes:

1. Vehicle hovering at approximately 3 metres before GCS connection loss.
2. Gazebo vehicle state after QGroundControl was closed.
3. PX4 terminal showing GCS connection loss and failsafe activation.
4. RTL, landing and disarming messages.

## Conclusion

**TEST-005 PASSED.**

PX4 successfully detected the loss of the QGroundControl connection and executed the configured failsafe recovery procedure.

The vehicle entered Hold, initiated Return-to-Launch, landed automatically and disarmed safely.

This confirms that the simulated PX4 failsafe system provides an effective safety response to Ground Control Station connection loss.

## Evidence Images


### 1. Vehicle Hovering at 3 Metres Before GCS Loss

<img width="1724" height="990" alt="12" src="https://github.com/user-attachments/assets/e644a524-2838-47fd-b229-fbc5ed98bbfb" />


### 2. Gazebo Vehicle After GCS Connection Loss

<img width="1166" height="877" alt="1222" src="https://github.com/user-attachments/assets/977eb695-669a-4ed0-b09f-f53c46e97926" />


### 3. PX4 GCS Connection Loss and Failsafe Activation

<img width="1517" height="785" alt="123" src="https://github.com/user-attachments/assets/fce0b7b8-21b1-42df-a38d-39ea4b32cb43" />


### 4. RTL, Landing and Safe Disarming

<img width="1517" height="785" alt="123" src="https://github.com/user-attachments/assets/1a28b24c-cfd3-45b6-92f7-9628da0cd2c9" />
