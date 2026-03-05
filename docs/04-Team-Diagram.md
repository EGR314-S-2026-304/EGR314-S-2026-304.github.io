---
title: Block Diagram, Protocol, and Message Structure
---

## Team Block Diagram

![Block Diagram](image/314-Team304-TeamBlockDiagram.png)


**Figure 1**: Subsystem PCBs and Connections, PDF version [*here*](https://github.com/user-attachments/files/25704085/314-Team304-TeamBlockDiagram.drawio.pdf)

## Communication Sequence

``` mermaid
sequenceDiagram
  autonumber


  participant Roshan (OLED)
  participant Dylan (wifi)
  participant Quinn (motors)
  participant Telescope

  Roshan (OLED)-->>Dylan (wifi): Input Coordinates
  Dylan (wifi)->>Dylan (wifi): LED Blink (or not)
  Dylan (wifi)-->>Roshan (OLED): Display wifi status
  Dylan (wifi)->>Quinn (motors): Turn On Telescope
  Quinn (motors)->>Telescope: Move Scope (X,Y Motors)

  Roshan (OLED)-->>Quinn (motors): Adjust Scope
  Quinn (motors)->>Quinn (motors): Translate Input to Motor Signals
  Quinn (motors)->>Telescope: Move Scope (X,Y)

  Telescope-->>Quinn (motors): Data Received
  Roshan (OLED)->>Quinn (motors): Refresh Data (1s loop)
  Quinn (motors)-->>Roshan (OLED): Display Data on OLED
```

## Message Structure

| Message Type<br>byte 1-2<br>(uint16_t) | Description                                   |
| -------------------------------------- | --------------------------------------------- |
| 1                                      | WiFi Signal Received                          |
| 2                                      | Set Data Receiver Type (Web or In-person)     |
| 3                                      | Print User Input                              |
| 4                                      | Translate Coordinate Input to Motor Input     |
| 6                                      | Power Button Pushed                           |
| 7                                      | Set Motor X, Y                                |
| 8                                      | Set Roshan subsystem to On/Off                |

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
