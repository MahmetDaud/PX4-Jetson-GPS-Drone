# TEST-003 — RTL Altitude and Safe Recovery Verification

## Test Summary

| Item | Result |
|---|---|
| Test ID | TEST-003 |
| Date | 22 August 2026 |
| Environment | PX4 Software-in-the-Loop (SITL) |
| Simulator | Gazebo Sim |
| Vehicle | Gazebo x500 Quadcopter |
| Ground Station | QGroundControl Daily |
| Test Result | PASS WITH OBSERVATION |

## Objective

The objective was to verify the Return-to-Launch (RTL) altitude and Safe Recovery behavior of the simulated x500 quadcopter.

## Configuration Reviewed

| Setting | Value |
|---|---|
| Takeoff altitude | 10 m |
| RTL climb altitude | 30 m |
| RTL final action | Land immediately |
| Landing descent rate | 0.7 m/s |
| Disarm after landing | 2.0 s |
| Data-link loss action | Return mode |
| Data-link loss timeout | 10 s |
| RC/joystick loss action | Return mode |
| RC/joystick loss timeout | 0.5 s |
| Maximum flight time | Disabled (-1 s) |

## Test Procedure

1. Started PX4 SITL with the Gazebo x500 model.
2. Connected QGroundControl to PX4.
3. Took off to an altitude of 10 m.
4. Confirmed stable Hold mode.
5. Sent a Go-To-Location command.
6. Confirmed that the vehicle moved horizontally while maintaining approximately 10 m altitude.
7. Activated Safe Recovery.
8. Observed the RTL climb, return, descent and landing.
9. Confirmed that the vehicle landed and disarmed successfully.

## Observations

- The vehicle successfully took off and held 10 m altitude.
- The Go-To-Location command was executed successfully.
- Safe Recovery initiated Return-to-Launch behavior.
- The vehicle climbed above the original 10 m flight altitude during RTL.
- An altitude of approximately 15.9 m was observed during this test.
- The vehicle returned, landed and disarmed successfully.
- The final status was Ready and Hold at ground level.

## Explanation of RTL Altitude

The RTL altitude is independent of the mission or takeoff altitude.

The takeoff and Go-To-Location altitude was 10 m, while the configured RTL climb altitude was 30 m. Therefore, the vehicle climbing above 10 m during Safe Recovery was expected behavior and not a navigation failure.

The vehicle was not observed reaching exactly 30 m during this test.

## Result

**PASS WITH OBSERVATION**

Takeoff, Hold, Go-To-Location, Safe Recovery, Return-to-Launch, automatic landing and disarming operated successfully.

The RTL altitude configuration must always be reviewed before operating physical hardware.

## Evidence Collected

The following screenshots were recorded:

- Safety and RTL configuration
- Takeoff at 10 m
- Hold and Go-To-Location operation
- Safe Recovery operation
- Final Ready and Hold status after landing

## Safety Note

Before physical flight tests, the RTL altitude must be selected according to local obstacles, legal altitude limits and the test area. Battery and communication failsafe settings must also be verified.

## Conclusion

TEST-003 successfully verified the PX4 RTL altitude and Safe Recovery behavior. The vehicle returned, landed and disarmed correctly. The altitude increase above 10 m was caused by the configured RTL climb altitude and was expected.
