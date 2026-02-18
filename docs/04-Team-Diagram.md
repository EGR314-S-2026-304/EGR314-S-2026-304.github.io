---
title: Block Diagram, Protocol, and Message Structure
---

## Team Block Diagram

![](image/EGR314_Team304_BlockDiagram.drawio.png)

**Figure 1**: Subsystem PCBs and Connections, PDF version [*here*](EGR314_Team304_BlockDiagram.drawio.pdf)

## Communication Sequence

``` mermaid
sequenceDiagram
  autonumber
  actor WebUser
  WebUser-->>Dylan: Input Coordinates
  Dylan->>Dylan: LED blink
  Dylan->>x: Turn On Telescope
  x->>x: Translate Coordinates to Motor Input
  x->>Quinn: Move Camera along X, Y axis w/ Motors
  Quinn->>Roshan: Begin Recording Data w/ Camera and Hall Effect Sensor
  loop WebData
    Roshan->>Dylan: Send Data
    Dylan-->>WebUser: Data on App
    WebUser-->>Dylan: Data Received
    Dylan->>Dylan: Refresh data (1s)
  end
  actor InPersonUser
  InPersonUser-->>x: Adjust Camera View
  x->>x: Translate Input to Motor Input
  x->>Quinn: Move Camera along X, Y axis
  Quinn->>Roshan: Begin Recording
  loop ScreenData
    Roshan->>x: Send Data
    x-->>InPersonUser: Display Data on OLED
    InPersonUser-->>x: Data Received
    x->>x: Refresh data (1s)
  end
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

