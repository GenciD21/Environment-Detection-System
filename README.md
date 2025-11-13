# Environmental Detection Systems Overview

In this project, the goal is to create an IoT device that interfaces primarily with the **BME280 Sensor** to measure a combination of **humidity**, **pressure**, and **temperature**.  
The data will be streamed over the web to a host computer that will process it accordingly.

I'm writing this document because I often get stuck as projects grow larger and more complex.  
This time, I want to improve my organization and planning skills to work more efficiently.

---

## Component Overview

### The ESP32 and BME280

- **ESP32-S3:**  
  The ESP32 will serve as the main microcontroller for this project due to its versatility.  
  It will:
  - Collect sensor data  
  - Display it locally  
  - Send it over the web to the host computer

- **BME280:**  
  This sensor is highly versatile and well-documented.  
  It will collect humidity, pressure, and temperature data, which the ESP32 will read via **SPI**, process, and package for transmission.

---

### Other Peripherals

- **16x2 I²C LCD Display:**  
  A simple LCD will be used to display data locally.  
  I originally planned to use an SPI TFT display, but decided to simplify the setup to focus on building a complete and functional system first.

---

## Data Analysis Overview

As mentioned earlier, the **BME280** is capable of reading **humidity**, **pressure**, and **temperature** — a combination powerful enough to estimate **altitude** and even **predict short-term weather trends**.

### Ideas for Data Analysis

1. **Basic Statistical Measurements**  
   These will be plotted and stored before doing more complex analysis:  
   - Mean  
   - Median  
   - Mode *(less relevant due to data variability)*  
   - Range  
   - Variance  
   - Standard Deviation  

2. **Linear Regression**  
   Use linear regression to predict future temperature, pressure, and humidity.  
   This is a good starting point for modeling and pattern recognition with sensor data.

3. **Random Forest / XGBoost for Rainfall Prediction**  
   An idea inspired by ChatGPT — using ensemble models to predict rainfall or other weather events.  
   I’ll need to explore this further, but it could be an interesting direction for the project.
