# Temperature And Humidity Data Logger

In this project, we ahave made a temperature and relative humidity data logger. Arduino is the brain of this project. DHT22 sensor is used for sensing temperature and relative humidity. Arduino Uno is programmed to read temperature, humidity values from DHT22 sensor and save it to a file in an SD Card. So whenever required we can take the SD Card for viewing data. Here we will take data from SD card and import it to excel to plot graphs.

## Components Required

1. Arduino Uno
2. SD Card Module
3. DHT22 Temperature and Humidity Sensor
4. SD Card (Higher than 8GB)
5. Breadboard
6. Connecting wires

## Circuit Diagram


## Micro SD Card Reader Module – Pinout


## Explanation

First of all, we will connect the SD Card module to the Arduino. Arduino can do read write operations on SD Card via SPI protocol. So we need to connect the SD card module to SPI pins of Arduino, which are pins 13, 12, 11 and 10. Since it is using SPI protocol, it won’t work if we connect SD card module to normal digital IO pins. So make connections as below.

1. SD Card Module Ground to Arduino Ground
2. VCC of the module to 5V output of Arduino
3. MISO of module to pin 12 of Arduino
4. MOSI of module to pin 11 of Arduino
5. SCK of module to pin 13 of Arduino
6. CS of module to pin 10 of Arduino
7. Then we can connect the DHT22 to the Arduino.
8. Connect VCC of DHT22 to 5V output of Arduino
9. Ground to ground of Arduino
10. Data pin of DHT22 to pin 8 of Arduino

