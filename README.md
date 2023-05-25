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



# CONCLUSIONES
_esta es conclusión_
