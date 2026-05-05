---
title: Project Version 2.0
---

# Project Version 2.0

Version 2.0 of the project would focus on improving communication reliability, system robustness, and debuggability compared to Version 1.0. While the current system demonstrates basic functionality, it relies on a simple UART protocol and limited error handling, which can lead to unreliable behavior during real operation.

One major improvement would be redesigning the communication protocol. Instead of a simple "AZ…BY" format, Version 2.0 would use a structured message such as:
AZ,SENDER,RECEIVER,COMMAND,DATA,CHECKSUM,BY.  
This allows clear separation of fields, easier parsing, and the addition of error detection through a checksum. Acknowledgement (ACK) messages would also be added so subsystems can confirm successful communication.

To expand system functionality, a new sensing subsystem such as a camera or IR sensor could be integrated. This would allow the system to detect environmental conditions, motion, or object presence, enabling more advanced features beyond manual input. For example, an IR sensor could automatically trigger system responses, while a camera could provide higher-level data for decision making. This would make the system more autonomous and practical for real-world applications.

To improve system reliability, a fail-safe mode would be implemented. If invalid or corrupted messages are received, the system would disable outputs and display an error state. A watchdog timer could also be added to automatically reset the system if it becomes unresponsive.

Debuggability would be significantly improved by enhancing the OLED interface to display system status, last received message, and error conditions. Additional hardware features such as status LEDs, a debug header, and reset/boot buttons would make testing and troubleshooting easier.

New software functions such as message validation, parsing, checksum verification, and error handling would modularize the code and improve maintainability.

Overall, Version 2.0 would transform the project from a working prototype into a more robust and reliable embedded system by improving communication structure, adding sensing capabilities, enhancing safety mechanisms, and strengthening debugging support.