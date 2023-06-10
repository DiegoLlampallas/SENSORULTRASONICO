## CESAR AUGUSTO GONZALEZ INFANTE
# Práctica ESP32 con DHT22 y LCD

## Programación

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

   lcd.setCursor(0, 0);
  lcd.print("HOLA              ");
  lcd.setCursor(0, 1);
  lcd.print("CESAR GONZALEZ  ");

  delay(1000);
}
```

## Librerías

1. **DHT sensor library for ESPx**
2. **LiquidCrystal I2C**
![](https://github.com/CesarG16/DHT22LCD/blob/main/eje1.png?raw=true)
## Conexión

![](https://github.com/CesarG16/DHT22LCD/blob/main/eje2.png?raw=true)

## Funcionamiento del programa

![](https://github.com/CesarG16/DHT22LCD/blob/main/eje3.png?raw=true)
![](https://github.com/CesarG16/DHT22LCD/blob/main/eje4.png?raw=true)


## Evidencias

[Página](https://wokwi.com/projects/367164531602566145)


# Créditos

Desarrollado por Ing. Cesar Augusto Gonzalez Infante

- [GitHub](https://github.com/CesarG16)