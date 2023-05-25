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
