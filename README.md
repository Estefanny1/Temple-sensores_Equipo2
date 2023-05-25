# Temple-sensores_Equipo2
Realización de proyecto con sensores.

# Depto de Sistemas y Computación
# Ing. En Sistemas Computacionales
# SISTEMAS PROGRAMABLES 23a


# OBJETIVO:


# CÓDIGO
```python
## Depto de Sistemas y Computación
## Ing. En Sistemas Computacionales
## SISTEMAS PROGRAMABLES 23a
## Autor (es): 
- Cruz Barradas Estefanny
- Duran Martinez Jesus Alejandro
- Estradra Dominguez Sergio
- Gutierrez Martinez Juan Andres 
- Virgen Pulido Jose Angel
- Garcia Armijo Araceli Elizabeth 
- Hernandez Aguiar Juan Carlos
- ...

## Repositorio:  Temple-sensores Equipo2
## Fecha de revisión:   99/99/2023
## Objetivo: Realizar un proyecto con distintos sensores, para tener conocimiento de estos, de como se programan y se manipulan con diferentes maneras de uso.
##   

## TODO: (pendientes sin resolver)
##
##
## In Progress: (resueltos parcialmente)
##
##
## Complete:  (Ya terminado), borrar estos mensajes.
```
--------------------------------------------------------------------------------

# SENSOR KY-032 Avoidance
Este sensor enciende o apaga un LED en función de si se detecta un obstáculo o no. 
## CODIGO
```python
import machine

led_pin = machine.Pin(13, machine.Pin.OUT)      # LED pin on Raspberry Pi Pico
detector_pin = machine.Pin(3, machine.Pin.IN)   # obstacle avoidance sensor interface

while True:
    val = detector_pin.value()  # Read value from sensor
    if val == 0:  # When the sensor detects an obstacle, the LED on Raspberry Pi Pico lights up
        led_pin.on()
    else:
        led_pin.off()
```
## PRUEBA 2
SENSOR KY-032 Avoidance

![images](https://github.com/elizabethAEGA2/elizabeth/blob/main/GITHUB/IMG_7569.jpg)

# SENSOR KY-027
El progrma detecta la inclinación. El LED externo se enciende cuando se detecta inclinación y se apaga cuando no hay inclinación.
## CODIGO 
```python
from machine import Pin
import utime

led = Pin('LED', Pin.OUT) 

detect = machine.Pin(27, machine.Pin.IN)#Salida para el pin de inclinacion ky-027 2pcs light cup
led1 = machine.Pin(1, machine.Pin.OUT)#salida para el led 

while True:
    detect_value = detect.value()
    led1.value(detect_value)
    utime.sleep(1)
   ```
## PRUEBA 3
 SENSOR KY-027
 
 ![images](https://github.com/elizabethAEGA2/elizabeth/blob/main/GITHUB/343690953_925479425179974_5976787584261593921_n.jpg)

## PRUEBA 4
 # SENSOR KY-015
 ## CODIGO  
```
 import dht12
import machine
import time
import ssd1306


sda_pin = machine.Pin(4) # GPIO4 como SDA
scl_pin = machine.Pin(5) # GPIO5 como SCL
i2c = machine.I2C(-1, sda=sda_pin, scl=scl_pin)
oled = ssd1306.SSD1306_I2C(128, 32, i2c)


dht_pin = machine.Pin(12, machine.Pin.IN, machine.Pin.PULL_UP) # GPIO12 como entrada
dht_sensor = dht12.DHT12(dht_pin)

while True:
    
    dht_sensor.measure()
    temp = dht_sensor.temperature()
    hum = dht_sensor.humidity()
    
    
    oled.fill(0)
    oled.text("TEMP: {:.1f} C".format(temp), 0, 0)
    oled.text("HUM: {:.1f} %".format(hum), 0, 10)
    oled.show()
    
    time.sleep(2) # Espera 2 segundos antes de la próxima lectura

 ```
 ## PRUEBA 5
 # SENSOR JOYSTICK KY-023
 
![348365414_102903776145097_6553385901693308597_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/717a3ebe-164f-4f94-8b28-beacc2c39914)
![346143104_1416278552528717_8067493179608268175_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/d8fd48c7-6a22-4323-ac05-0a8e904558e9)
![346141970_558720809779490_2711893195499034884_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/b42e1a3f-37af-4dbb-b594-bd262234c80b)
![346134530_128701950178092_2663836356191803617_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/ee88c81f-1e3e-4dfc-9dd1-e438dc1f1602)

 ## CODIGO
 ```python
 from machine import Pin, ADC, PWM
import utime
from machine import Pin, I2C
from ssd1306 import SSD1306_I2C
from time import sleep_ms
import utime as time
from dht import DHT11, InvalidChecksum



#oled cordanadas de tamaño
ANCHO = 128
ALTO = 64


xAxis = ADC(Pin(27))
yAxis = ADC(Pin(26))
button = Pin(17,Pin.IN, Pin.PULL_UP)

led_left = Pin(14, Pin.OUT)
led_middle = Pin(15, Pin.OUT)
led_right = Pin(12, Pin.OUT)
led_up = Pin(16, Pin.OUT)
led_down = Pin(13, Pin.OUT)

i2c = I2C(1,scl = Pin(19), sda = Pin(18))
oled = SSD1306_I2C(ANCHO, ALTO, i2c)

buzzer = PWM(Pin(6))
buzzer.freq(500)

while True:
    oled.fill(0)

    xValue = xAxis.read_u16()
    yValue = yAxis.read_u16()
    buttonValue = button.value()
    xStatus = "middle"
    yStatus = "middle"
    buttonStatus = "not pressed"

    led_left.value(0)
    led_down.value(0)
    led_up.value(0)
    led_right.value(0)
    led_middle.value(1)

                  #Sensor temperatua


# Check the x and y Value to determine the status of the joystick
    if buttonValue == 0:
        buttonStatus = "pressed"
        led_middle.value(0)
        oled.text("presionado",0,30)
        buzzer.duty_u16(0)

    if xValue <= 600:
        xStatus = "left"
        led_left.value(1)
        led_middle.value(0)
        oled.text("Abajo",5,30)
        buzzer.duty_u16(0)
        

    if xValue >= 60000:
        xStatus = "right"
        led_right.value(1)
        led_middle.value(0)
        oled.text("Arriba",5,10)
        


    if yValue <= 600:
        yStatus = "up"
        led_up.value(1)
        led_middle.value(0)
        oled.text("Izquierda",5,30)

    if yValue >= 60000:
        yStatus = "down"
        led_down.value(1)
        led_middle.value(0)
        oled.text("Derecha",5,30)

    oled.show()

    print("X: " + xStatus + ", Y: " + yStatus + "  button status: " + buttonStatus)
    utime.sleep(0.2)
 ```
 ## PRUEBA 6
 Mostrar en pantalla oled la intencidad de luz que resive la fotoresistensia
 # SENSOR Photoresistor module KY-018
 ![348357057_243998028309667_1399446362090185094_n (1)](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/6f790ac9-e42a-4c95-8442-dae7b309f8c4)

  ## CODIGO
 ```python
from machine import ADC, Pin, I2C
from time import sleep

from machine import Pin, I2C
from ssd1306 import SSD1306_I2C

ANCHO = 128
ALTO = 64
i2c = I2C(1,scl = Pin(19), sda = Pin(18))
oled = SSD1306_I2C(ANCHO, ALTO, i2c)

photoPIN = 26

def readLight(photoGP):
    photoRes = ADC(Pin(26))
    
    light = photoRes.read_u16()
    
    light = round(light/65535*100,2)
    return light

while True:
    oled.fill(0)
    
    oled.text("light: " + str(readLight(photoPIN)) +"%",0,30)
    sleep(1) # set a delay between readings
    oled.show()
 ```
 ## PRUEBA 7
  # SENSOR  KY-029
 ![348358169_206814208836019_8304376646058096095_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/073d68bd-b066-4e97-84a2-622b6f705a71)
```Python
from machine import  Pin,


led = Pin(25, Pin.OUT)
led.value(1)
```
 ## PRUEBA 8
  # SENSOR  passive buzzer ky-006
  ![346123738_126117127143614_5675418411842338542_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/ee570301-6b4d-4245-b471-084c00ee668e)

 ```Python
 from machine import Pin, PWM
from utime import sleep
buzzer = PWM(Pin(15))

tones = {
"B0": 31,
"C1": 33,
"CS1": 35,
"D1": 37,
"DS1": 39,
"E1": 41,
"F1": 44,
"FS1": 46,
"G1": 49,
"GS1": 52,
"A1": 55,
"AS1": 58,
"B1": 62,
"C2": 65,
"CS2": 69,
"D2": 73,
"DS2": 78,
"E2": 82,
"F2": 87,
"FS2": 93,
"G2": 98,
"GS2": 104,
"A2": 110,
"AS2": 117,
"B2": 123,
"C3": 131,
"CS3": 139,
"D3": 147,
"DS3": 156,
"E3": 165,
"F3": 175,
"FS3": 185,
"G3": 196,
"GS3": 208,
"A3": 220,
"AS3": 233,
"B3": 247,
"C4": 262,
"CS4": 277,
"D4": 294,
"DS4": 311,
"E4": 330,
"F4": 349,
"FS4": 370,
"G4": 392,
"GS4": 415,
"A4": 440,
"AS4": 466,
"B4": 494,
"C5": 523,
"CS5": 554,
"D5": 587,
"DS5": 622,
"E5": 659,
"F5": 698,
"FS5": 740,
"G5": 784,
"GS5": 831,
"A5": 880,
"AS5": 932,
"B5": 988,
"C6": 1047,
"CS6": 1109,
"D6": 1175,
"DS6": 1245,
"E6": 1319,
"F6": 1397,
"FS6": 1480,
"G6": 1568,
"GS6": 1661,
"A6": 1760,
"AS6": 1865,
"B6": 1976,
"C7": 2093,
"CS7": 2217,
"D7": 2349,
"DS7": 2489,
"E7": 2637,
"F7": 2794,
"FS7": 2960,
"G7": 3136,
"GS7": 3322,
"A7": 3520,
"AS7": 3729,
"B7": 3951,
"C8": 4186,
"CS8": 4435,
"D8": 4699,
"DS8": 4978
}


song = ["E5","G4","E5","G4","E5","G4","E5","G4","E5","G4","E5","G4","D4","B6","D4","GS5","A4","GS5","E5","A4","D4","E5","D4","E5","D4","E5","D4","E5","B6","E5","B6"]

def playtone(frequency):
    buzzer.duty_u16(1000)
    buzzer.freq(frequency)

def bequiet():
    buzzer.duty_u16(0)

def playsong(mysong):
    for i in range(len(mysong)):
        if (mysong[i] == "P"):
            bequiet()
        else:
            playtone(tones[mysong[i]])
        sleep(0.3)
    bequiet()
playsong(song)
 ```
 # PRUEBA 9
![images](https://github.com/tectijuana/git-fundamentos-JoseAPulido/blob/main/imagenes/20230508_145314.jpg)

![images](https://github.com/tectijuana/git-fundamentos-JoseAPulido/blob/main/imagenes/20230508_145307.jpg)

# SENSORES  ky-005 ir emission
Tiene como objetivo controlar el sensor KY-005 de emisión infrarroja utilizando una Raspberry Pi Pico. Es un codigo 
sencillo para demostrar el funcionamiento
## CODIGO

```python
import machine
import utime

# Configurar el pin GPIO para controlar el sensor KY-005
pin_ir = machine.Pin(16, machine.Pin.OUT)

while True:
    # Encender el emisor infrarrojo
    pin_ir.on()
    print("Emisor infrarrojo encendido")

    # Esperar un breve momento
    utime.sleep(1)

    # Apagar el emisor infrarrojo
    pin_ir.off()
    print("Emisor infrarrojo apagado")

    # Esperar antes de repetir el ciclo
    utime.sleep(5)

   ```
## PRUEBA 10
SENSORES  ky-005 ir emission
![images](https://github.com/elizabethAEGA2/elizabeth/blob/main/GITHUB/348366292_780297140471972_674763039964703554_n.jpg)
![images](https://github.com/elizabethAEGA2/elizabeth/blob/main/GITHUB/348857920_202336795963427_5231867576821245411_n.jpg)

## PRUEBA 11 


# Sensor KY-012 buzzer y KY-027 2pcs light cup
El sensor Ky-027 funciona con movimiento de inclinación si el sensor se inclina y el mercurio deja de tener conexión con el circuito enciende el led como en la imagen, para este le agregamos un buzzer para que hiciera sonido si se activaba el sensor de inclinación.

# Código

```python
from machine import Pin
import utime
led = Pin('LED', Pin.OUT) 
buzzer = Pin(0, Pin.OUT) #salida para el sensor KY-012 Buzzer
detect = machine.Pin(27, machine.Pin.IN)#Salida para el pin de inclinacion ky-027 2pcs light cup
led1 = machine.Pin(1, machine.Pin.OUT)#salida para el led 
while True:
    detect_value = detect.value()
    buzzer.value(detect_value)
    led1.value(detect_value)
    buzzer.value(detect_value)
    utime.sleep(1)
  
```
## PRUEBA 12

# Sensor KY-026 Flame y KY-012 buzzer
El sensor KY-026 lo utilizamos para detectar flamas y activa el buzzer conectado para hacer la simulacion de alarma contra incendio o para detectar fuego.
En la prueba lo activamos con un encendedor.

# Codigo

```python
from machine import Pin
import utime
buzzer = Pin(0, Pin.OUT) #salida para el sensor KY-012 Buzzer
flame_sensor = Pin(16, Pin.IN)#salida para el sensor KY-026flame
utime.sleep(2)
while True:
   if flame_sensor.value() == 1:
       print("Flame Detected")
       buzzer.value(2)
       utime.sleep(3)
   else:
       print("No Flame")
       buzzer.off()
       utime.sleep(1)  
utime.sleep(0.1)
```
## PRUEBA 13

# sensor KY-002 shock
El sensor KY-002 funciona con una resistencia de movimiento, al ser movido el objeto o el sensor detecta una vibraciones e indica que el sensor tuvo movimiento.
La prueba se realizo activando un led cada que tuviera movimiento el sensor.

# Codigo

```python
import machine
import utime

SENSOR_PIN = 27
LED_PIN = 0

sensor = machine.Pin(SENSOR_PIN, machine.Pin.IN, machine.Pin.PULL_UP)
led = machine.Pin(LED_PIN, machine.Pin.OUT)

while True:
    estado = sensor.value()
    if estado == 0:
        led.value(1)
        print("Movimiento detectado")
        utime.sleep(2)
    else:
        led.value(0)
```

## PRUEBA 14 
# Sensor KY-001 18B20 TEMP
El sensor de temperatura KY-001 se programo para recibir la temperatura actual y su conexion, solo se ocupan las librerias para detectar la temperatura.

# Codigo
```python
import machine
import onewire
import ds18x20
# Declaración del pin de entrada que está conectado con el módulo del sensor
KY001_Signal_PIN = 4
# Configuración de las bibliotecas
oneWire = onewire.OneWire(machine.Pin(KY001_Signal_PIN)) # Crear un objeto OneWire utilizando el pin de entrada
sensors = ds18x20.DS18X20(oneWire) # Crear un objeto DS18X20 utilizando el objeto OneWire
# Inicialización de la salida serial
uart = machine.UART(0, 9600)
print("KY-001 medición de temperatura")
# Inicialización del sensor
roms = sensors.scan() # Escanear los dispositivos conectados al bus OneWire
sensors.convert_temp() # Iniciar la conversión de temperatura en el sensor
# Bucle principal del programa
while True:
    # Iniciar la medición de temperatura...
    sensors.convert_temp()
    machine.delay(750)
    # ... y mostrar la temperatura medida
    for rom in roms:
        temp = sensors.read_temp(rom)
        print("Temperatura: ", temp, "C")
    machine.delay(1000) # Esperar 1 segundo antes de la siguiente medición
```

# CONCLUSIONES
_esta es conclusión_
