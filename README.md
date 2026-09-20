3-Axis Accelerometer Telemetry & Data Logging System
An embedded C++ prototype of a 3-axis accelerometer Data Acquisition system designed to model real-time dynamic vehicle motion tracking. This repository contains both a live virtual hardware simulation and full embedded firmware for telemetry streaming and high-frequency local SD card data logging.
System Architecture & Files
This repository contains three main components:
1. Circuit Schematic (tinkercad_circuit file)
-  layout of the 3-axis accelerometer simulation built in Tinkercad using an Arduino Uno R3 and precision potentiometers.
- Utilizes strict DC color coding (Red = +5V, Black = GND, Blue = Analog Signal Traces (A0, A1, A2)).
2. serial_telemetry.cpp
- Embedded C++ firmware designed for real-time telemetry streaming over Serial.
- Samples 10-bit analog signals at 50 Hz, converts raw ADC values into physical g-force units via floating-point linear transformations, and outputs formatted telemetry.
3. sd_card_logger.cpp
- C++ firmware extension that interfaces with an SPI microSD module (SPI.h / SD.h).
- Buffers calibrated g-force readings into CSV format on local storage for non-volatile post-test vehicle dynamic analysis.
Features & Technical Specifications
Microcontroller: Arduino Uno R3 (ATmega328P)
Sampling Frequency: 50 Hz (20 ms interval loop)
Signal Pipeline: 10-bit ADC -> Floating-point Voltage Conversion -> Calibrated g-Force Mapping
Communication: UART Serial @ 9600 baud / SPI for SD storage
Wiring Standards: Industry-standard DC color-coding conventions for clear documentation and maintenance
Getting Started
Running the Simulation
1. Open the Tinkercad Circuit Model.
2. Load the code from serial telemetry cpp into the Tinkercad code editor.
3. Start the simulation and open the Serial Monitor or Serial Plotter to observe dynamic g-force outputs as potentiometer levels change.
Hardware Deployment
1. Flash sd_card_logger.cpp onto an Arduino Uno connected to a physical 3-axis analog accelerometer (e.g., ADXL335) and SPI microSD module.
2. Insert a FAT16/FAT32 formatted microSD card.
3. Power the system to start logging raw telemetry directly to datalog.csv.
License
This project is licensed under the MIT License.
