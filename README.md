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

# PRUEBA 
![](https://www.snapon.co.za/images/thumbs/default-image_550.png)

![](https://www.snapon.co.za/images/thumbs/default-image_550.png)

# CONCLUSIONES
_esta es conclusión_
