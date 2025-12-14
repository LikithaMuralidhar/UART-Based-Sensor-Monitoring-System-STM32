# UART-Based Sensor Monitoring System (STM32)

## Overview

This project implements a UART-controlled sensor monitoring system on an STM32 microcontroller using the STM32 HAL library.  
The system simulates temperature and humidity sensors and allows interaction through a serial terminal using text-based commands.

Users can start or stop monitoring, read sensor data on demand, configure sampling intervals, and select output formats.

---

## Features

- UART-based command-line interface
- Simulated temperature and humidity sensors
- Continuous and on-demand data transmission
- Configurable sampling interval
- Multiple output formats:
  - Text
  - CSV
  - JSON
- Interrupt-driven UART reception
- Robust command parsing and error handling

---

## Hardware and Software Requirements

### Hardware
- STM32 microcontroller (STM32U5 series or compatible)
- USB-to-UART interface
- Serial terminal (Tera Term, PuTTY, Minicom)

### Software
- STM32CubeIDE
- STM32 HAL drivers
- arm-none-eabi-gcc toolchain

---

## UART Configuration

- UART Instance: USART1
- Baud Rate: 115200
- Data Bits: 8
- Stop Bits: 1
- Parity: None
- Flow Control: None

---

## Supported Commands

| Command | Description |
|------|------------|
| READ | Read sensor values
| START | Start continuous monitoring |
| STOP | Stop continuous monitoring |
| SET_INTERVAL `<sec>` | Set interval (1–60 seconds) |
| FORMAT TEXT | Set output format to text |
| FORMAT CSV | Set output format to CSV |
| FORMAT JSON | Set output format to JSON |
| HELP | Display available commands |

## Example Output

Text
```bash
Temperature: 25 C, Humidity: 60 %
```

CSV
```bash
25,60
```

JSON
```bash
{"temp":25,"hum":60}
```

## Program Flow

1. Initialize system clock, GPIO, ICACHE, and UART
2. Display startup message on UART
3. Receive user commands using UART interrupts
4. Parse and execute commands in the main loop
5. Simulate sensor data using system ticks
6. Format and transmit data via UART

---

## Code Structure

- `main.c`
  - UART initialization and interrupt handling
  - Command parsing
  - Sensor simulation
  - Data formatting and transmission
- Uses STM32 HAL UART callbacks
- Non-blocking and interrupt-driven design

---

## Error Handling

- Detects unknown commands
- Prevents command buffer overflow
- Validates command parameters
- Sends error messages over UART

---

## Future Enhancements

- Integration of real sensors (I2C/SPI)
- Persistent storage using Flash or EEPROM
- RTOS-based task scheduling
- Data integrity checks (CRC)
- Support for multiple sensor nodes

---

## Author

Likitha Muralidhar


