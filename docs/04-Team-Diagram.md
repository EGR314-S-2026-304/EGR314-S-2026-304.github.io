---
title: Block Diagram, Protocol, and Message Structure
---

## Team Block Diagram

![](image/EGR314_Team304_BlockDiagram.drawio.png)

## Communication Sequence

``` mermaid
sequenceDiagram
  autonumber
  Alice->>John: Hello John, how are you?
  loop Healthcheck
      John->>John: Fight against hypochondria
  end
  Note right of Hafsa: Rational thoughts!
  Hafsa-->>Alice: Great!
  Hafsa->>Bob: How about you?
  Bob-->>Hafsa: Jolly good!
  create actor P as In-PersonUser
  Hafsa->>P: Hi
```

## Message Structure

---
config:
  packet:
    bitsPerRow: 16
    bitWidth: 64
---
packet-beta
title Message
0: "0x41"
1: "0x5a"
2: "Source ID"
3: "Dest ID"
4-61: "Message (Variable Length <= 58 Bytes)"
62: "0x59"
63: "0x42"
