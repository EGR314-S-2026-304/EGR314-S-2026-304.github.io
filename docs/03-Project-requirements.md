---
title: Project Requirements
---

## Overview
The following sections document the requirements that Team 304 should meet. Below is a table listing requirements in which we feel are sufficient for this project. We have also included other useful information about each requirement, as well as whether the requirement is among our stretch goal.

### How our features became requirements
  - **Camera**: The telescope needs to observe and record visual data of celestial objects, meaning that a camera that can record the night sky is needed for this project. To better fit the needs of the user, our team will experiment with other features for the camera, such as low-light filters and built-in storage.
  - **Motor**: Motors are required to automatically rotate the camera to be able to observe and track celestial objects.
  - **WI-FI Connectivity**: Wi-fi will be implemented in this project in order to remotely transmit data recorded by the camera to the user. An app, website, or other piece of software would need to be designed so that the user can easily access the data as well as send commands to the telescope.
  - **User Interface**: The automated telescope will have a phyical user interface so that it can be set-up and operated by the user without internet connection. This would include components such as an on and off switch, LCD screen, and LEDs.
  - **Housing**: To protect the telescope from outside elements, a housing will need to be modeled and built around the features listed above.

### Requirement Table

| **Requirement Description** | **Measure of<br> Threshold** | **Target<br>Measure** |**Stretch<br>Requirement<br>(Y-N)**|
|-----------------------------| ----------------- | ----------------- | :-----: |
| Surface mounted, 3.3V switching power regulator | 3.2 Volts | 3.3 Volts | No |
| Surface mounted microcontroller | 1 PIC or ESP | 8-bit PIC | No |
| Wireless Communication | Able to send or receive a Wi-Fi data | Send and receive Wi-Fi Data to MQTT | no |
| Housing | Full 3d printed housing for all components | Safely stores and looks like an EV-Scope | Yes |
|*The rest are items your modules need to support the task you are covering for the team's device.* | --- | --- | **NO** |

## Assigning Responsibilities
| **Member Name** | **Requirement Description** |
|---------------| -----------------------------------|
|    Michael   |                Selection and Switch (Change this)                       |
|    Hafsa     |                User Interface (Change this)                        |
|    Dylan     |               The system shall include an onboard Wi Fi communication module capable of establishing a stable connection to a local wireless network in order to transmit camera image data to a remote user device and receive control commands for telescope operation.                   |
|    Roshan    |                The system shall include a camera system capable of capturing and recording high-quality visual data of celestial objects, supporting low-light imaging, and interfacing with the onboard processor for storage and remote transmission. The camera shall be mounted securely to the telescope assembly, provide sufficient resolution and sensitivity to detect stars and planets, and allow for user control over capture settings via the telescope’s control interface.                        |
|    Quinn     |                Motor System (Change this)                        |
