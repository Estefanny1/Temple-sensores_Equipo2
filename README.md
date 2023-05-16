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
# SENSORES  KY-038 Small Sound Y KY-034 7 COLOR FLASH
Se combinaron dos sensores para que cuando el sensor small sound detectara sonido el sensor color flash prendiera en todos sus colores 
este es el codigo que se utilizo para esta practica.
## CODIGO

```python
import machine
import utim

# Configurar los pines
sound_pin = machine.Pin(26, machine.Pin.IN)
led_pin = machine.Pin(1, machine.Pin.OUT)

# Bucle principal
while True:
    # Leer el valor del sensor de sonido
    sound_value = sound_pin.value()

    # Encender el LED si se detecta un sonido
    if sound_value == 1:
        led_pin.on()
    else:
        led_pin.off()

    # Retardo para evitar lecturas rápidas y estables
    utime.sleep(0.1)
   ```
## PRUEBA
SENSORES  KY-038 Small Sound Y KY-034 7 COLOR FLASH
![images](https://github.com/elizabethAEGA2/elizabeth/blob/main/GITHUB/Captura%20de%20pantalla%202023-05-15%20181105.png)

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
## PRUEBA
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
## PRUEBA 
 SENSOR KY-027
 
 ![images](https://github.com/elizabethAEGA2/elizabeth/blob/main/GITHUB/343690953_925479425179974_5976787584261593921_n.jpg)

 # PRUEBA 
![](https://www.snapon.co.za/images/thumbs/default-image_550.png)

![](https://www.snapon.co.za/images/thumbs/default-image_550.png)

## PRUEBA 
 # SENSOR KY-015
 ## CODIGO  
 import dht12
import machine
import time
import ssd1306

# Configuración de la pantalla OLED
sda_pin = machine.Pin(4) # GPIO4 como SDA
scl_pin = machine.Pin(5) # GPIO5 como SCL
i2c = machine.I2C(-1, sda=sda_pin, scl=scl_pin)
oled = ssd1306.SSD1306_I2C(128, 32, i2c)

# Configuración del sensor DHT12
dht_pin = machine.Pin(12, machine.Pin.IN, machine.Pin.PULL_UP) # GPIO12 como entrada
dht_sensor = dht12.DHT12(dht_pin)

while True:
    # Lectura de la temperatura y humedad
    dht_sensor.measure()
    temp = dht_sensor.temperature()
    hum = dht_sensor.humidity()
    
    # Actualización de la pantalla OLED
    oled.fill(0)
    oled.text("TEMP: {:.1f} C".format(temp), 0, 0)
    oled.text("HUM: {:.1f} %".format(hum), 0, 10)
    oled.show()
    
    time.sleep(2) # Espera 2 segundos antes de la próxima lectura

 
 
 

 # PRUEBA 
![](https://www.snapon.co.za/images/thumbs/default-image_550.png)

![](https://www.snapon.co.za/images/thumbs/default-image_550.png)


# CONCLUSIONES
_esta es conclusión_
