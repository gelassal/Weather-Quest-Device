# 🌤️ Embedded Weather Quest

An IoT weather station built on the TM4C123 LaunchPad that fetches real-time weather data from the OpenWeatherMap API and displays it on a color LCD.

**Course:** CECS 447 — Embedded Systems, Spring 2024  
**Team:** Nathan Wong, Youssef Shafeek, George Elassal

---

## Overview

The system connects to a Wi-Fi access point via the CC3100 SimpleLink module, accepts user input through a serial terminal (TeraTerm), queries [openweathermap.org](https://openweathermap.org) for weather data, and renders the results — including animated weather icons — on an ST7735R 128×160 color LCD.

---

## Features

- Query weather by **city name**, **city ID**, **geographic coordinates**, or **ZIP code**
- Displays **temperature**, **min/max temp**, **humidity**, and **weather description**
- Animated weather icons for Rain, Clouds, and Clear conditions
- Dual output: ST7735 color LCD + TeraTerm serial terminal
- UART-based user input interface

---

## Hardware

| Component | Description |
|---|---|
| TM4C123 LaunchPad | Main microcontroller |
| CC3100 SimpleLink | Wi-Fi module for internet connectivity |
| ST7735R LCD | 128×160 color display |

**Pin connections:** GND, VCC, Reset, D/C, TFT_CS, MOSI, SCK, LITE (see schematic in project report)

---

## Software Dependencies

- TivaWare / TM4C123 driverlib
- CC3100 SimpleLink SDK
- ST7735 LCD driver (`ST7735.c`)
- OpenWeatherMap API (free account required)

---

## Setup & Configuration

1. Create a free account at [openweathermap.org](https://openweathermap.org/appid) and obtain an API key.
2. In `ST7735main.c`, update the following defines:
   ```c
   #define SSID_NAME  "YourNetworkName"
   #define SEC_TYPE   SL_SEC_TYPE_WPA
   #define PASSKEY    "YourPassword"
   ```
   Replace the `APPID` string with your own API key.
3. Build and flash the project onto the TM4C123 LaunchPad.
4. Open TeraTerm at **115200 baud**.
5. Press **Reset** on the board — a menu will appear.

---

## Usage

```
Welcome to my Embedded Weather Quester!
Please choose your query criteria:
 1. City Name
 2. City ID
 3. Geographic Coordinates
 4. Zip Code
```

Select an option, enter the requested input, and weather data will be displayed on both the LCD and terminal. Press **Reset** to query a new city.

---

## Demo

📹 [Watch on YouTube](https://youtu.be/E8pBWBL6dJ4?si=ZVKtIqKU3YKD7FdY)

---

## File Structure

```
├── ST7735main.c      # Main application logic (Wi-Fi, HTTP, UART, LCD output)
├── ST7735.c          # ST7735R LCD driver
├── ST7735.h          # LCD driver header
├── bmps.h            # Bitmap data for weather animations
└── README.md
```

---

## License

This project was developed for academic purposes at California State University, Long Beach.
