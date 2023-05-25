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
