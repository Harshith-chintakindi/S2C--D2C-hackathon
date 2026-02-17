# S2C--D2C-hackathon
Secure IR Sensor Data Transmission Using Zynq-7000 (ZedBoard)
 Project Description (20 Detailed Points)

Project Overview
This project implements a secure real-time sensor data transmission system using the Zynq-7000 (XC7Z020) FPGA on the ZedBoard platform.

Objective
The primary goal is to capture digital data from an IR obstacle detection sensor, encrypt the data inside FPGA programmable logic (PL), and transmit the encrypted data securely via UART to a PC.

Hardware Platform
The system is implemented on the ZedBoard featuring the Zynq-7000 SoC (XC7Z020-1CLG484C), utilizing only the Programmable Logic (PL) section.

Clock Configuration
A 100 MHz onboard clock (Pin Y9) is used as the system clock for encryption logic and UART transmission timing.

Sensor Interface
A digital IR obstacle detection sensor is connected to PMOD JA1 (Pin Y11) and operates at 3.3V logic level.

Data Acquisition
The IR sensor output is sampled and converted into an 8-bit data format before being processed by the encryption module.

Encryption Module
The project includes a custom hardware encryption module (e.g., XOR-based encryption) implemented in Verilog to secure the sensor data before transmission.

Hardware-Level Security
Encryption is performed directly inside FPGA hardware, ensuring that transmitted data is not in plaintext.

UART Transmission Module
A UART transmitter module is implemented in RTL to send encrypted 8-bit data serially to the PC.

UART Configuration
The UART operates at 9600 baud rate and transmits data at regular 1-second intervals.

Pin Configuration
All I/O pins are defined in the XDC constraints file:

clk → Y9

ir_in → Y11

tx → AA11

debug_led → T22

Debug Mechanism
An onboard LED (Pin T22) is used to visually indicate real-time sensor status for debugging purposes.

External Communication Interface
A 3.3V USB-to-TTL converter is used to interface FPGA UART TX (JA2 – Pin AA11) with a PC.

PC-Side Decryption
A Python script using PySerial reads the encrypted UART data and performs software-side decryption to recover original sensor information.

Secure Data Flow Architecture

IR Sensor → FPGA (Encryption) → UART → USB-TTL → PC (Decryption)


Pure RTL Implementation
The entire system is implemented in Verilog using Vivado without using the Processing System (PS), making it a pure programmable logic design.

Low Resource Utilization
The design uses minimal FPGA resources, making it scalable for integration into larger secure embedded systems.

Scalability
The architecture can be extended to:

AES hardware encryption

Multi-sensor integration

Bidirectional secure communication

IoT-based secure monitoring

Applications

Secure IoT sensor nodes

Industrial automation monitoring

Secure embedded communication systems

Defense-grade sensor transmission systems

Educational Value
This project demonstrates practical implementation of:

FPGA-based encryption

UART protocol design

Hardware-software co-design

Secure digital communication systems
