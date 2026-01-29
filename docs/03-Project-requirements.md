---
title: Project Requirements
---

## Overview
The following sections document the requirements that Team 304 should meet. Below is a table listing requirements in which we feel are sufficient for this project. We have also included other useful information about each requirement, as well as whether the requirement is among our stretch goal.

### How our features became requirements
  - **Camera**: The telescope needs to observe and record visual data of celestial objects, meaning that a camera that can record the night sky is needed for this project. To better fit the needs of the user, our team will experiment with other features for the camera, such as low-light filters and built-in storage.
  - **Motor**: Motors are required to rotate the camera to be able to observe and track celestial objects.
  - **WI-FI Connectivity**: Wi-fi will be implemented in this project to remotely transmit data recorded by the camera to the user. An app, website, or other piece of software would need to be designed so that the user can easily access the data as well as send commands to the telescope.
  - **User Interface**: The automated telescope will have a physical user interface so that it can be set up and operated by the user without an internet connection. This would include components such as an on and off switch, LCD screen, and LEDs.
  - **Housing**: To protect the telescope from outside elements, a housing will need to be modeled and built around the features listed above.

### Requirement Table

| **Requirement Description** | **Measure of<br> Threshold** | **Target<br>Measure** |**Stretch<br>Requirement<br>(Y-N)**|
|-----------------------------| ----------------- | ----------------- | :-----: |
| ... | ... | ... | No |
| ... | ... | ... | No |
| User Interface | User is able to input commands manually and device operates according to each command and sensor data | User and sensor inputs cause outputs to sensors and physical interface | No |
| Housing | Full 3d printed housing for all components | Safely stores and looks like an EV-Scope | Yes |
| Scope Movement (motor) | Able to be precisely moved | 0.5 millimeters | Yes |

## Assigning Responsibilities
| **Member Name** | **Requirement Description** |
|---------------| -----------------------------------|
|    Michael   |                  Exposure and gain are essential to a camera. Each helps the photos in the processing stage and also help the telescope in general. The system will use some sort of light sensor and a set of small motors to control the camera shutter, which should help with light entering the camera chamber.                       |
|    Hafsa     |                A physical user interface is needed to turn on and off the telescope, adjust settings, alert user, and guarantee functionality if device is unable to establish Wi Fi connection.                   |
|    Dylan     |               The system shall include an onboard Wi Fi communication module capable of establishing a stable connection to a local wireless network in order to transmit camera image data to a remote user device and receive control commands for telescope operation.                   |
|    Roshan    |                The system shall include a camera system capable of capturing and recording high-quality visual data of celestial objects, supporting low-light imaging, and interfacing with the onboard processor for storage and remote transmission. The camera shall be mounted securely to the telescope assembly, provide sufficient resolution and sensitivity to detect stars and planets, and allow for user control over capture settings via the telescope’s control interface.                        |
|    Quinn     |                The system will include a motor system that will be calibrated to automatically/remotely move. With this, the user can set the EV-Scope so that it can track distant objects, as well as easily maneuver the scope while maintaining the safety of the user and the scope itself.                        |
