---
title: Block Diagram, Protocol, and Message Structure
---

## Team Block Diagram

![]()<img width="2409" height="799" alt="314-Team304-TeamBlockDiagram drawio" src="https://github.com/user-attachments/assets/6de21c1a-1afc-4d95-a31b-eb8a54b17aef" />


**Figure 1**: Subsystem PCBs and Connections, PDF version [*here*](https://github.com/user-attachments/files/25704085/314-Team304-TeamBlockDiagram.drawio.pdf)

## Communication Sequence

``` mermaid
sequenceDiagram
  autonumber


  participant Roshan (OLED)
  participant Dylan (wifi)
  participant Telescope
  participant Quinn (motors)

  Roshan-->>Dylan: Input Coordinates
  Dylan->>Dylan: LED Blink
  Dylan->>Telescope: Turn On Telescope
  Telescope->>Quinn: Move Scope (X,Y Motors)

  Roshan-->>Telescope: Adjust Scope
  Telescope->>Telescope: Translate Input to Motor Signals
  Telescope->>Quinn: Move Scope (X,Y)

  Telescope-->>Roshan: Display Data on OLED
  Roshan-->>Telescope: Data Received
  Telescope->>Telescope: Refresh Data (1s loop)
```

## Message Structure

| Message Type<br>byte 1-2<br>(uint16_t) | Description                                   |
| -------------------------------------- | --------------------------------------------- |
| 1                                      | WiFi Signal Received                          |
| 2                                      | Set Data Receiver Type (Web or In-person)     |
| 3                                      | Print User Input                              |
| 4                                      | Translate Coordinate Input to Motor Input     |
| 5                                      | Translate Potentiometer inputs to Motor Input |
| 6                                      | Power Button Pushed                           |
| 7                                      | Set Motor X, Y                                |
| 8                                      | Set Roshan subsystem to On/Off                |
| 9                                      | Transmit Compressed Image                     |
| 10                                     | Transmit Hall Effect Data                     |

Message Type 1:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t) |
| ------------------- | ---------------- |
| 01                  | wifi (bool)      |

Message Type 2:

| Byte 1-2 (uint16_t) | Byte 3-58 (char)   |
| ------------------- | ------------------ |
| 02                  | string             |

Message Type 3:

| Byte 1-2 (uint16_t) | Byte 3-58 (char) |
| ------------------- | ---------------- |
| 03                  | string           |

Message Type 4:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t) | Byte 4-5 (uint16_t) |
| ------------------- | ---------------- | ------------------- |
| 04                  | X (uint8_t)      | Y (uint16_t)        |

Message Type 5:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t) | Byte 4-5 (uint16_t) |
| ------------------- | ---------------- | ------------------- |
| 05                  | X (uint8_t)      | Y (uint16_t)        |

Message Type 6:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t)  |
| ------------------- | ----------------- |
| 06                  | Button (bool)     |

Message Type 7:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t) | Byte 4-5 (uint16_t) |
| ------------------- | ---------------- | ------------------- |
| 07                  | X (uint8_t)      | Y (uint16_t)        |

Message Type 8:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t)         |
| ------------------- | ------------------------ |
| 08                  | subsystemState (bool)    |

Message Type 9:

| Byte 1-2 (uint16_t) | Byte 3-58 (uint8_t)  |
| ------------------- | -------------------- |
| 09                  | CameraData (uint8_t) |

Message Type 10:

| Byte 1-2 (uint16_t) | Byte 3 (uint8_t)   |
| ------------------- | ------------------ |
| 10                  | HallData (uint8_t) |

