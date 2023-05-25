Led laser

```python
import machine
import time

# Configuración del pin GPIO
led_pin = machine.Pin(7, machine.Pin.OUT)

led_pin.value(0)
print('Led prendido')
# Espera 1 segundo
time.sleep(10)

# Apaga el LED
led_pin.value(1)
print('Led apagado')

```

![](https://scontent.ftij1-2.fna.fbcdn.net/v/t1.15752-9/344300433_256959086837359_952338236435345702_n.png?_nc_cat=103&ccb=1-7&_nc_sid=ae9488&_nc_ohc=bBfD9If0DjYAX8lo8CL&_nc_ht=scontent.ftij1-2.fna&oh=03_AdREC2fYyh8bN-zrEjFjlTBdyQ0eZrONQfkC-qv5NfWijg&oe=648946F0)

![](https://scontent.ftij1-2.fna.fbcdn.net/v/t1.15752-9/349058431_574392501404259_3150481255012632406_n.jpg?_nc_cat=100&ccb=1-7&_nc_sid=ae9488&_nc_ohc=PBhjY3E078AAX9A2uN1&_nc_ht=scontent.ftij1-2.fna&oh=03_AdSjhtd2jgymXjBagP_4ngjNNcczPugfKsJf6OB2FLfBhQ&oe=6496487D)
