# Práctica-No.3-DHT-con-LCD
Dentro de este repositorio se muestra la manera de programar una ESP32 con el sensor DHT11 y además, que los datos obtenidos se muestran en una pantalla LCD.
## Introducción
### Descripción
La **ESP32** se utiliza en un entorno de adquisición de datos, por lo cual en esta práctica utilizaremos un sensor **DHT11** para obtener registros de temperatura y humedad del entorno. Dichos registros serán mostrados de manera visual en una pantalla LCD. Para esta practica se hace uso de un simulador llamado [WOKWI](https://wokwi.com/projects/new/esp32).
## Material necesario
Para realizar esta práctica necesitas lo siguiente

- [WOKWI](https://wokwi.com/projects/new/esp32)
- Tarjeta ESP32
- Sensor DHT11
- LCD 16x2 (I2C)
## Instrucciones
### Requisitos previos
Para poder hacer uso de este repositorio se requiere entrar a la plataforma de [WOKWI](https://wokwi.com/projects/new/esp32).
### Instrucciones de preparación del entorno
1. Abrir la terminal de programación y colocar el siguiente código:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
}

```
2. Instalar la libreria de **DHT Sensor library for ESPx** y **LiquidCrystal I2C** como se muestra en la siguiente imagen
![](https://github.com/AbrahamCH1/Practica-No.3-DHT-con-LCD/blob/main/Captura%20de%20pantalla%20(290).png?raw=true)
![](https://github.com/AbrahamCH1/Practica-No.3-DHT-con-LCD/blob/main/Captura%20de%20pantalla%20(296).png?raw=true)

3. Hacer la conexion de **DHT11** y **LCD 16x2 (I2C)** con la **ESP32** como se muestra en la siguente imagen.
![](https://github.com/AbrahamCH1/Practica-No.3-DHT-con-LCD/blob/main/Captura%20de%20pantalla%20(297).png?raw=true)

### INSTRUCCIONES DE OPERACIÓN
1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Visualizar los datos en la pantalla LCD.
4. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11** 
## Resultados
Cuando haya funcionado, se podrán observar los valores dentro de la pantalla LCD.
![]()

# CRÉDITOS
Desarrollado por Ing. Abraham Contreras Herrera
[GITHUB](https://github.com/AbrahamCH1)
