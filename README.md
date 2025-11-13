# Envrionmental Detection Systems Overview

  In this project, the plan is to create an IoT device that allows the user to interface primarily with the BME280 Sensor in order to get a combination of humidity, pressure and temperature sensor. With it, we'll stream the data over the web to a host computer that well proccess the data accordingly. I'm mainly writing this document because I feel like I get stuck on a lot of project as they've gotten bigger over the years. This time, I'm hoping to publish my organization and planning skills to be more efficient. 


# Component Overiview 

* The ESP32 and BME280
  * ESP32-S3: The ESP32 well likely be the suitable microcontroller for this project given its versality. We'll be using it as the host controller in this scenario. It'll do all of the managing of collecting sensor data, displaying it locally, and sending it over the web!
    
  * BME280: This sensor not only is highly versatile but some very good documentation in reagrds to it's usability. We'll be using this to collect sensor data, constantly cycling and packaging the data accordingly with the ESP32 via SPI.
 
* Other Perpherials
  * An 16x2 I2C LCD will be used in order to display the data in a simple manner locally. I planed to use an SPI TFT Display but those are an hassle to deal with to some capacity and the main focus is going to be on creating the full system in general.
 
# Data Analysis Overview

*As said previously, the BME280 is a pretty powerful controller in terms of its capability to read humdiity, pressure, and temperature data. This combination alone is enough to read alititude and possible even predict the weather! Here's some ideas for what can we predict
  *Common Statistic Measurements that can be plotted and saved - I think this one is pretty basic but necessary before anything is done in a complicated manner. 
     *This includes the following:
        - Mean - 
        - Median
        - Mode - (But given the variation, probably not really relevant)
        - Range 
        - Variance 
        - Standard Deviation 
  *Utilizing Linear Regression to predict future, temperature, pressure, and humidty - I think this is a pretty intersting one and my 
 
    

 

  
        





