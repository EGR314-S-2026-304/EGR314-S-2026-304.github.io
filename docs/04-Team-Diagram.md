---
title: Block Diagram, Protocol, and Message Structure
---

## Team Block Diagram

![](image/EGR314_Team304_BlockDiagram.drawio.png)

## Communication Sequence

``` mermaid
sequenceDiagram
  autonumber
  actor WebUser
  WebUser-->>Dylan: Input Coordinates
  Dylan->>Hafsa: Turn On
  Hafsa->>Hafsa: Translate Coordinates to Motor Input
  Hafsa->>Quinn: Move Camera along X, Y axis
  Quinn->>Roshan: Begin Recording
  loop WebData
    Roshan->>Dylan: Send Data
    Dylan-->>WebUser: Live Data
  end
  actor InPersonUser
  InPersonUser-->>Hafsa: Adjust Camera View
  Hafsa->>Hafsa: Translate Input to Motor Input
  Hafsa->>Quinn: Move Camera along X, Y axis
  Quinn->>Roshan: Begin Recording
  loop ScreenData
    Roshan->>Hafsa: Send Data
    Hafsa-->>InPersonUser: Display Data
  end
```

## Message Structure

| Message Type<br>byte 1-2<br>(uint16_t) | Description |
| -------------------------------------- | ----------- |
| 1                                      | x           |
