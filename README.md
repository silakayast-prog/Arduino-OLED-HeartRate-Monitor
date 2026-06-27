# Arduino-OLED-HeartRate-Monitor
#  Arduino-Based MAX30102 Heart Rate (BPM) Monitor with OLED Display Integration

This project is an embedded system application that utilizes the **MAX30102** photoplethysmography (PPG) sensor to measure real-time heart rate (BPM) from a finger. The data is displayed with a dynamic animation on a **128x32 OLED (I2C)** screen, providing audio feedback via a **Buzzer** every time a heart pulse is detected.

---

##  Hardware Components

* **Microcontroller:** Arduino UNO (or any compatible board)
* **Sensor:** MAX30102 Heart Rate and Pulse Oximeter Sensor (I2C)
* **Display:** 128x32 OLED Display (SSD1306, I2C)
* **Feedback:** Passive/Active Buzzer (Digital Pin 3)

---

##  Technical Highlights & Features

Instead of simply printing raw sensor data, the following engineering approaches were implemented to ensure a stable and professional output:

1. **Dynamic Finger Detection:** Infrared (IR) data readings are continuously monitored (`irValue > 7000`) to detect whether a finger is placed on the sensor. If no finger is detected, the user is prompted on the screen.
2. **Moving Average Algorithm:** To eliminate sudden fluctuations and noise in BPM readings, a rolling array with `RATE_SIZE = 4` is maintained. The system calculates the average of the last 4 readings to display a smooth, accurate, and stable BPM value.
3. **Visual & Audio Animation:** The moment a heartbeat is detected, the heart icon on the screen expands (`logo3_bmp`), and a brief 100ms beep is generated using `tone()` and `noTone()` functions, simulating a real medical device environment.

---

##  Key Learning Outcomes

Through this project, I have gained practical experience in:
* **I2C Protocol Management:** Driving both the OLED display and the MAX30102 sensor concurrently on the same bus without conflicts using the `Wire.h` library.
* **Bitmap Graphics Processing:** Storing custom-designed heart icons (`bmp`) directly in the Arduino's flash memory using `PROGMEM` and rendering them dynamically.
* **Time Management & Calculations:** Utilizing the hardware `millis()` function to precisely measure the duration between two consecutive heartbeats and translating it into a mathematical BPM formula.

---

##  File Structure

* `HeartRateMonitor.ino` - Main Arduino source code.
* `README.md` - Project documentation.
