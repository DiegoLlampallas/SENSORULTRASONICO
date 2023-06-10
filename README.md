# Práctica ESP32 con ULTRASONICO de Diego Llampallas

## Programación

```

#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 13;   //Pin digital 3 para el Echo del sensor

const int DHT_PIN = 15;



LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);
void setup() {
 Serial.begin(9600);
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
    lcd.init();
  lcd.backlight();
}





void loop()
{

  long t; //timepo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(1000);          //Hacemos una pausa de 100ms

  lcd.setCursor(0, 0);
  lcd.print("Distancia: " + String(d) +"Cm ");
   lcd.setCursor(0, 1);
  lcd.print("Diego Llampallas");
  delay(1000);          //Hacemos una pausa de 100ms
 
}

```
![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/11.png?raw=true)

## Partes
1. ![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/5.png?raw=true)
2. ![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/6.png?raw=true)
3. ![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/7.png?raw=true)
4. ![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/8.png?raw=true)

## Libreria
![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/9.png?raw=true)

## Conexión

![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/10.png?raw=true)

## Funcionamiento

![](https://github.com/DiegoLlampallas/SENSORULTRASONICO/blob/main/12.png?raw=true)

## Evidencias

[Página](https://wokwi.com/projects/367158771640158209)


# Créditos

Desarrollado por Ing. Diego Alberto Llampallas Vega

- [GitHub](https://github.com/DiegoLlampallas)