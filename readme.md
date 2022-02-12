# Krystian Peplinski
# Technika mikroprocesorowa - projekt

## Temat:

- Miernik temperatury działający w zakresie od -55°C do 125°C.

## Lista elementów:

- płytka Arduino Uno
- płytka stykowa
- przewody
- Moduł wyświetlacza LCD
- rezystor 10kΩ
- czujnik temperatury (Działa w zakresie od -55°C do 125°C. Zasilany jest napięciem od 3,0 V do 5,5 V)

## Linki:
[https://allegro.pl/oferta/zestaw-l-arduino-uno-starter-kit-prezent-9924753145](https://allegro.pl/oferta/zestaw-l-arduino-uno-starter-kit-prezent-9924753145)

[https://botland.com.pl/cyfrowe-czujniki-temperatury/165-czujnik-temperatury-ds18b20-cyfrowy-1-wire-tht-5904422366513.html](https://botland.com.pl/cyfrowe-czujniki-temperatury/165-czujnik-temperatury-ds18b20-cyfrowy-1-wire-tht-5904422366513.html)

## Schemat (wykonany w programie fritzing):

![schemat tmp](https://user-images.githubusercontent.com/93950820/153689029-58769ab3-31d8-41a1-bb30-d4678e8442fa.jpg)


## Kod:
Napisany dla programu Arduino: https://www.arduino.cc/en/software
```
#include <OneWire.h>
 #include <DallasTemperature.h>
 #include <Wire.h>
 #include <LiquidCrystal_I2C.h>
 LiquidCrystal_I2C lcd(0x27,16,2);
 #define ONE_WIRE_BUS 5
 OneWire oneWire(ONE_WIRE_BUS);
 DallasTemperature sensors(&oneWire);
  float Celcius=0;
 void setup(void)
 {
  Serial.begin(9600);
  sensors.begin();
  lcd.init();
  lcd.backlight();
  lcd.print("Temperatura:");
 }
 void loop(void)
 {
  sensors.requestTemperatures();
  Celcius=sensors.getTempCByIndex(0);
  Serial.print(" C ");
  Serial.print(Celcius);
   lcd.setCursor(0, 1);
   lcd.print(Celcius);
   lcd.setCursor(6, 1);
   lcd.print("C");
   lcd.setCursor(9, 1);
  delay(1000);
 }
 ```
 ## Efekt końcowy:
 Połączenie na płytkach:
 ![połączenie przewodów](https://user-images.githubusercontent.com/93950820/153688355-ed23ed3b-4cc3-44b5-a99c-144ae602b289.jpg)
 Wyświetlanie temperatury:
 ![wyświetlacz](https://user-images.githubusercontent.com/93950820/153688427-c6b5e8bb-8864-4769-8f1a-183be957870a.jpg)
Film pokazujący działanie czujnika (na czujniku położony jest palec, aby temperatura stale wzrastała):
https://www.youtube.com/watch?v=2N7m-c9jxME

## Wnioski:
Czujnik temperatury można by umieścić na dłuższych przewodach, aby móc go wystawić na zewnątrz i w ten sposób sprawdzać temperaturę np. zimą przed wyjściem z domu.
