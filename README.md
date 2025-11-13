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

### Top Level Overview of the ESP32, Sensor, Display, and Host:
![Top Level Overview](overhead_graphic.png)

### Circuit and Pin Level Overview of the ESP32, Sensor, Display:

![Circuit and Pin Level Overview](pin_diagram.png)


---


# Technical Talk with Peripherals and Host through ESP32

It can be easy with a solid plan to go straight into programming - however not understanding some of the fundementals of how these components are connected leads to poor results later on. With the goal of this project being to sharpen my system design and embedded skills, we'll use part to discuss the technical aspect of the ESP connecting to the BME280, the algorithm involved in it, ESP32 and the LCD Display, as well as the ESP32/Host WebSocket Connection. 

---

## ESP32 and BME280 
  * I think this is an easier part that can be rushed - I mean, sensor interfacing and getting real world data is one the most exciting parts. However; previous attempts and easily interfacing with sensors can get messy for a number of reasons. I leading cause would obviously be imporper documenation, inexperience, etc, and therefore proper understanding of the BME280 and connection is necesasry for the project to succeed.
       * General BME280 Overview:
           * Physical/Electrical Characteristics:
               * 1.71V to 3.6V(So 3.3V is more then enough)
               * Extra Note: The PCB im using contaiend the decoupling capacitors necessary for us to do the protocols, otherwise I'd this here as well.
           *  Sensor Interafacing General:
               *  The Sensor Cotains 3 Modes: 2'b00 - Sleep Mode(Self Explanatory), 2'b01 - Forced Mode(Preform One Measurement, Store Result and Sleep), 2'b10 - Normal Mode (Perpetual Fetching of all Measurements, to be used mostly)
               *  Genearl Note: during normal mode, we can actually disable temperature readings for specific measurements if we desire.
               *  An important aspect of the BME280 is the IIR Filter - used mainly for pressure noise reduction because the external environment can quickly change it. There's a couple of modes we'll look into later
               *  Because of the number of settings, the BME280 datasheet actually has predetermined settings(That we should configure, of course)! In this scenario of weather modeling, we'll be using the following:
                       * Weather monitoring Setting:
                               * Mode Settings: Forced, 1 sample / minute,
                               * Over Sampling Settings: pressure ×1, temperature ×1, humidity ×1,
                               * IIR Filter Settings: filter off

  






