# Sensor KY-002 shock
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
