# Quadcopter-Prototype
This project is a ground-up quadcopter prototype focused on building and validating the core control stack needed for stable flight from scratch using regular arduino, and all the additional required modules (Transmitter/Receiver, Gyro, etc.). The main goal was to connect motor outputs to sensor feedback and test a closed-loop stabilization approach before moving to full-frame integration.

## Project Goals
- Build a ground-up quadcopter control stack on a regular Arduino, integrating the required modules (gyro, transmitter/receiver, motor control hardware) and components available.
- Implement and validate a closed-loop stabilization algorithm in C++, using real gyro feedback to drive motor outputs.
- Design a reliable sensor-to-actuator pipeline (gyro → control loop → motor commands) that can be tested and tuned on real hardware before full-frame integration.
- Develop a custom RC transmitter/receiver from scratch using Arduino + NRF24 (with joysticks and supporting circuitry) to support manual control as an alternative to automated flight.
- Prototype the hardware interfaces needed for expansion, including prototype PCBs and an attempted DIY brushless ESC approach with recycled brushless DC motors from old Hard discs.
- Establish a clear path to full integration: scaling from single-axis bench testing to multi-axis stabilization with additional ESCs and sensors (GPS/altimeter) for future flight-ready behavior.

## What I built
- An Arduino-based control system written in C++ implementing a closed-loop control algorithm for stabilization.
- Prototype circuit boards used to interface the Arduino with the brushless motor/propeller control hardware.
- A basic hardware test setup that ties together the gyrometer (gyro) sensor output with motor speed control, allowing control-loop behavior to be tested with real signals (shown in demo MP4 video).
- Custom built RC remote and receiver module from scratch, using Arduino, NRF24 Wireless Transceiver module, joysticks, and other necessary circuit components, following a similar design to this here, with necessary modifications and alternate components (https://www.youtube.com/watch?v=aztm_8qGVfc&list=PLsR1AO4QH1AwEh7BZHamzsNBO-Ud-pGBW&index=3).
- Attempted to build a brushless ESC (electronic speed controller) from scratch using an arduino and a custom PCB, following the design here (https://youtu.be/8LXPcJD6hEA?si=JXzT3ylQ1kq5TrVN), but was unsuccessful due to the unavailability of some components and limited PCB making ability.

## Quadcopter testing demo
Check MP4 demo file in repo, or follow this link: https://drive.google.com/file/d/1NxJxWkp-EyR-reV-OZMwFn3o3bTLC3V4/view?usp=sharing

## How it works
- The Arduino reads angular rate data from the gyrometer sensor.
- Sensor readings are processed to estimate motion dynamics and generate control corrections.
- The control loop updates motor commands to adjust propeller speed in response to measured rotation, with the intent of damping unwanted motion and improving stability.

## Current status
Development was paused at the control-loop testing stage (due to the inavailability of components such as 2 additional ESCs), specifically validating the feedback loop between the gyro readings and motor response. The emphasis at this point was on making sure the sensor-to-actuator pipeline was reliable and that control outputs behaved as expected under different test conditions.

## Next steps
- Tune control parameters and filtering to improve stability and reduce noise sensitivity.
- Expand from single-axis testing to multi-axis stabilization with all necessary additional components.
- Integrate additional sensors (GPS, Altimeter,etc.) and move toward full flight-ready integration through automated flight path or transmitter sinal.
