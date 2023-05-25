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
## Fecha de revisión:   25/05/2023
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
