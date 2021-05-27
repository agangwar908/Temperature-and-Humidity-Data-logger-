#include <SD.h>
#include <SPI.h>
#include "DHT.h"

#define DHTPIN 8
#define DHTTYPE DHT22

long seconds=00;
long minutes=00;
long hours=00;

int CS_pin = 10;

DHT dht(DHTPIN, DHTTYPE);
File sd_file;

void setup()  {
  Serial.begin(9600);
  pinMode(CS_pin, OUTPUT);
  dht.begin();
  // SD Card Initialization
  if (SD.begin())  {
    Serial.println("SD card is initialized. Ready to go");
  } 
  else  {
    Serial.println("Failed");
    return;
  }

  sd_file = SD.open("data.txt", FILE_WRITE);

  if (sd_file)  {
    Serial.print("Time");
    Serial.print(",");
    Serial.print("Humidity");
    Serial.print(",");
    Serial.print("Temperature_C");
    Serial.print(",");
    Serial.print("Temperature_F");
    Serial.print(",");
    Serial.println("Heat_index");

    sd_file.print("Time");
    sd_file.print(",");
    sd_file.print("Humidity");
    sd_file.print(",");
    sd_file.print("Temperature_C");
    sd_file.print(",");
    sd_file.print("Temperature_F");
    sd_file.print(",");
    sd_file.println("Heat_index");
  }
  sd_file.close(); //closing the file
} 

void loop()  {
  sd_file = SD.open("data.txt", FILE_WRITE);
  if (sd_file)  {
    senddata();
  }
  // if the file didn't open, print an error:
  else  {
    Serial.println("error opening file");
  }
  delay(1000);
}

void senddata()  {
  for(long seconds = 00; seconds < 60; seconds=seconds+2)  {
    float temp = dht.readTemperature(); //Reading the temperature as Celsius and storing in temp
    float hum = dht.readHumidity();     //Reading the humidity and storing in hum
    float fah = dht.readTemperature(true);
    float heat_index = dht.computeHeatIndex(fah, hum);

    sd_file.print(hours);
    sd_file.print(":");
    sd_file.print(minutes);
    sd_file.print(":");
    sd_file.print(seconds);
    sd_file.print(",  ");
    sd_file.print(hum);
    sd_file.print(",    ");
    sd_file.print(temp);
    sd_file.print(",      ");
    sd_file.print(fah);
    sd_file.print(",      ");
    sd_file.println(heat_index);

    Serial.print(hours);
    Serial.print(":");
    Serial.print(minutes);
    Serial.print(":");
    Serial.print(seconds);
    Serial.print(",  ");
    Serial.print(hum);
    Serial.print(",    ");
    Serial.print(temp);
    Serial.print(",       ");
    Serial.print(fah);
    Serial.print(",      ");
    Serial.println(heat_index);

    if(seconds>=58)  {
      minutes= minutes + 1;
    }

    if (minutes>59)  {
      hours = hours + 1;
      minutes = 0;
    }

    sd_file.flush(); //saving the file

    delay(2000);
  }
  sd_file.close();   //closing the file
}
