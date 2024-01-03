# UDS Client Message Management Library Development Requirements
## 1. Introduction
### 1.1 Purpose
The UDS Client Message Management Library is a software solution designed to streamline the implementation of Unified Diagnostic Services (UDS) client functionality on Controlled Area Network (CAN) enabled devices. As an integral part of the automotive diagnostic ecosystem, the library facilitates the communication of standardized diagnostic messages for vehicle maintenance and diagnostics. By offering a comprehensive set of features, the UDS Client Message Management Library aims to empower developers with a reliable and efficient toolset, enabling seamless integration of UDS communication into their applications.
### 1.2 Scope
The scope of this document encompasses the detailed requirements and specifications for the development of the UDS Client Message Management Library. From message encoding and decoding to CAN communication, session handling, and error reporting, the library aims to provide a robust foundation for UDS client operations. Additionally, the document outlines the supported diagnostic services, customization options, and compliance considerations necessary for successful library implementation.

## 2. Functional Requirements
| ID | Description |
| - | - |
| 1 | DLC of CAN messages should be selectable for sending UDS requests. The first option should be "always use 8-byte DLC" and the other option should be "fit DLC depending on UDS request length." |
| 2 | The library should support standard and extended CAN formats. |
| 3 | Baud rate should be selectable with options: 125 kbps, 250 kbps, 500 kbps, 1 Mbps. |
| 4 | There should be an additional delay between consecutive frames. The delay time should be set by the developer who uses the library. |
| 5 | There should be sync and async functions for all UDS services. |
| 6 | The timer callback function should be set by the developer. The timer's period should be 1 ms. UDSClient_SoftTimer shall create new timers with an ID and callback functions. |
| 7 | All UDS negative response codes should be added. Each UDS function should return a success or negative response code or CAN error." |
| 8 | If the UDS functions encounter a CAN error, they should be retried. The maximum retry counter should be configurable. |
| 9 | All configurable options that related to UDS should be stored in a structure. |
| 10 | If the UDS response has data, the data should be written to the buffer that is the input of the function. |
| 11 | CAN configuration should be set by the developer who uses the library. The "send CAN message" function and the "receive CAN message" callback function should be set by the developer. The library must not directly control any hardware or driver. |
| 12 | The logging system should be separate with log level, such as: NONE, TRACE, DEBUG, INFO, WARNING, ERROR, FATAL. |
| 13 | The logging system should be configurable in one header file. The logging level should be selectable for each C file. |
| 14 | This library can use the system logger, so the UDS client logger function should call the system logger with a log description. Also, log levels should be configurable with functions. |

## 3. External Interface Requirements

## 4. Non-functional Requirements
| ID | Description |
| - | - |
| 1 | All functions should be commented for doxygen format. After the development, doxygen document will be created. |
