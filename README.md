Descriere generala:
Acest proiect reprezinta un ceas smart capabil sa colecteze si sa afiseze date.Datele sunt afisaye pe un display E-INK si pot fi stocate pe un card SD
Sistemul este alimentat de o baterie LiPo si include management de energie eficient pentru untilizare portabila.

Diagrama bloc este gasita in imagini.
Functionalitate hardware
  Alimentare
    Intrare prin USB-C
    Controller MCP73832 pentru incarcare LiPo
    Bateria LiPo alimenteaza sistemul
    Sunt doua ramuri de tensiune:
      3.3V(LDO) 
      5V(Boost converter)->senzori PM si CO2
  Microcontroller
  ESP32-C3 gestioneaza 
    citirea senzorilor
    comunicarea cu display-ul
    stocarea pe SD
    input-ul de la butoane

Interfete utilizate
interfata    Componente
SPI          E-Ink display, SD card
UART         PM sensor, CO₂ sensor
I2C          Temp/RH sensor, Fuel Gauge, Haptic Driver
GPIO         Butoane

Conectare componente
  CS
  CLK
  MOSI
  DC
  RST
  BUSY

SD CARD
  partajat pe același bus SPI cu E-Ink

PM SENSOR(UART)
  TX/RX către ESP32
  Alimentare 5V

CO2 SENSOR(UART)
  Interfata seriala
  Alimentare 5V

Temp/RH Sensor (I2C)
  SDA
  SCL

Fuel Gauge(I2C)
  Monitorizare
    tensiune baterie
    procent incarcare

Haptic Driver(I2C)
  Feedback utilizator

Butoane 
  3 GPIO-uri
  Configurate cu pull-up intern


PINOUT ESP32-C2

| Pin   | Funcție    |
|-----  |------------|
| GPIO0 | Button 1   |
| GPIO1 | Button 2   |
| GPIO2 | Button 3   |
| GPIO3 | I2C SDA    |
| GPIO4 | I2C SCL    |
| GPIO5 | SPI CLK    |
| GPIO6 | SPI MOSI   |
| GPIO7 | SPI MISO   |
| GPIO8 | SPI CS E-Ink |
| GPIO9 | SPI CS SD  |
| GPIO10 | UART TX   |
| GPIO11 | UART RX   |

Functionare sistem
1.Sistemul porneste din baterie sau USB
2.ESP32 initializeaza toate interfetele
3.Citeste date de la senzori
  PM
  C02
  temp/umiditate
4.Afiseaza datele pe E-INK
5.Salveaza datele pe SD CARD
6.Utilizatorul poate interactiona cu butoanele
7.Sistemul intra in sleep pentru econmisire energie


Design considerations
  Separare clara 3.3V/5V
  Filtrare alimentare senzori
  Rutare SPI comuna
  Protectie baterie
  


  



  
