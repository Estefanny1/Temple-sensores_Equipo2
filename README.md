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
## PRUEBA 1
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

 # PRUEBA 6
![images](https://github.com/tectijuana/git-fundamentos-JoseAPulido/blob/main/imagenes/20230508_145314.jpg)

![images](https://github.com/tectijuana/git-fundamentos-JoseAPulido/blob/main/imagenes/20230508_145307.jpg)


# CONCLUSIONES
_esta es conclusión_
