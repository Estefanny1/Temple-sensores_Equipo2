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
