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
