# UART

## Tools 

- Sigrok / Pulseview

This tool is used to analyze data from a logic analyzer or an oscilloscope using a graphical user interface (GUI).

## How to connect ?

First, we need to inspect the PCB and find test points or pads where we can connect. These points may look different depending on the PCB design.

<img width="395" height="478" alt="image" src="https://github.com/user-attachments/assets/4c0d3a2e-5ce4-4241-9bfb-18b2ebe4ff35" />

### Basic UART signals

GND – ground; always connect GND to GND (a common ground is required for proper communication)

RX – receive line (used when you want to read data from the device)

TX – transmit line (used when you want to send data to the device)

This is how analyzer device look:
<img width="1095" height="612" alt="image" src="https://github.com/user-attachments/assets/f1bebb16-26eb-4265-b8e8-db372258473b" />

If you only want to read data from the device, connect:

GND → GND

TX (device) → CH0 (logic analyzer)

## How to use PulseView ?

After connecting the logic analyzer, open PulseView to analyze the captured signals.

Most settings can be left as default. The most important parameter is the baud rate.

If you see Frame Errors, try changing the baud rate to the correct value.

A list of common UART baud rates (bit rates) can be found on Wikipedia.

<img width="476" height="548" alt="image" src="https://github.com/user-attachments/assets/c5d59186-8cf3-4afc-9410-618a4cddb62b" />

## How to determine the baud rate?

<img width="692" height="244" alt="image" src="https://github.com/user-attachments/assets/b21acd22-45e9-4564-aecd-b538dde2e3b2" />

To determine the correct baud rate, you need to measure the duration of one bit.

In this example, the measured frequency is approximately 14.285714 kHz.

Next, check which standard baud rate is closest to this value. In this case, it is:

14,400 bit/s (baud)

A list of standard UART baud rates is available here:

https://en.wikipedia.org/wiki/Serial_port
