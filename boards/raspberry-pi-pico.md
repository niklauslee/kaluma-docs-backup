# Raspberry Pi Pico

This page describes information about the Kaluma port for Raspberry Pi Pico.

supported modules: ...

## PWM

There are 16 PWM channels \(8 2-channel slices\). GPIO pins sharing a channel \(e.g. GPIO 0 and GPIO16\) cannot be used at the same time.

| GPIO | Channel | GPIO | Channel | GPIO | Channel |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 0A | 10 | 5A | 20 | 2A |
| 1 | 0B | 11 | 5B | 21 | 2B |
| 2 | 1A | 12 | 6A | 22 | 3A |
| 3 | 1B | 13 | 6B | 23 | 3B |
| 4 | 2A | 14 | 7A | 24 | 4A |
| 5 | 2B | 15 | 7B | 25 | 4B |
| 6 | 3A | 16 | 0A | 26 | 5A |
| 7 | 3B | 17 | 0B | 27 | 5B |
| 8 | 4A | 18 | 1A | 28 | 6A |
| 9 | 4B | 19 | 1B | 29 | 6B |

## I2C

Default values for I2C functions.

| Function | Default |
| :--- | :--- |
| I2C baudrate | 400,000 |
| I2C0 SCL | Pin 4 |
| I2C0 SDA | Pin 5 |
| I2C1 SCL | Pin 2 |
| I2C1 SDA | Pin 3 |

## SPI

Default values for SPI functions.

| Function | Default |
| :--- | :--- |
| SPI baudrate | 1,000,000 |
| SPI0 SCK | Pin 18 |
| SPI0 MOSI \(TX\) | Pin 19 |
| SPI0 MISO \(RX\) | Pin 16 |
| SPI1 SCK | Pin 10 |
| SPI1 MOSI \(TX\) | Pin 11 |
| SPI1 MISO \(RX\) | Pin 12 |

## UART

Default values for UART functions.

| Function | Default |
| :--- | :--- |
| UART baudrate | 115,200 |
| UART buffer size | 2048 |
| UART0 TX | Pin 0 |
| UART0 RX | Pin 1 |
| UART1 TX | Pin 8 |
| UART1 RX | Pin 9 |



