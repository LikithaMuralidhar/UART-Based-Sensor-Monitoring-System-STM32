**UART-Based Sensor Monitoring System (STM32)**
Overview

This project implements a UART-controlled sensor monitoring system on an STM32 microcontroller using the STM32 HAL library.
The system simulates temperature and humidity sensors, allows user interaction through a serial terminal, and supports configurable output formats and sampling intervals.

Users can control the system by sending commands over UART to start/stop monitoring, read sensor data on demand, change data formats, and configure sampling intervals.

**Features**

UART-based command-line interface (CLI)

Simulated temperature and humidity sensors

Continuous or on-demand sensor data transmission

Configurable sampling interval

Multiple output formats:

Plain Text

CSV

JSON

Interrupt-driven UART reception

Robust command parsing and error handling

**Hardware and Software Requirements**
Hardware

STM32 microcontroller (tested with STM32U5 series)

USB-to-UART connection

Serial terminal (Tera Term, PuTTY, Minicom, etc.)

Software

STM32CubeIDE

STM32 HAL drivers

C compiler (arm-none-eabi-gcc)

**UART Configuration**

UART Instance: USART1

Baud Rate: 115200

Data Bits: 8

Stop Bits: 1

Parity: None

Flow Control: None


**Command	Description**

READ	Read sensor values once
START	Start continuous sensor monitoring
STOP	Stop continuous monitoring
SET_INTERVAL <sec>	Set sampling interval (1–60 seconds)
FORMAT TEXT	Output in human-readable text
FORMAT CSV	Output in CSV format
FORMAT JSON	Output in JSON format
HELP	Display available commands
Example Outputs

TEXT Format
'''bash
Temperature: 25 C, Humidity: 60 %
'''

CSV Format
25,60

JSON Format
{"temp":25,"hum":60}

**Program Flow**

System initializes clock, GPIO, UART, and ICACHE

Startup message is sent over UART

UART receive interrupt collects user commands byte-by-byte

Commands are parsed and executed in the main loop

Sensor data is simulated using system tick timing

Data is formatted and transmitted over UART

**Code Structure**

main.c

UART initialization and interrupt handling

Command parsing logic

Sensor simulation

Output formatting

Uses STM32 HAL callbacks for UART reception

Non-blocking and interrupt-driven design

Error Handling

Detects unknown commands

Prevents buffer overflow

Validates command parameters

Provides clear error messages over UART

**Future Enhancements**

Replace simulated sensors with real hardware sensors

Add EEPROM or Flash logging

Integrate RTOS for task scheduling

Add CRC or checksum for data integrity

Extend commands for multi-sensor support
