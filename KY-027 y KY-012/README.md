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
