```python
import machine

# Configura el pin del potenciómetro
potentiometer_pin = machine.ADC(26)

# Bucle principal
while True:
    # Lee el valor analógico del potenciómetro
    potentiometer_value = potentiometer_pin.read_u16()

    # Imprime el valor leído
    print("Valor del potenciómetro:", potentiometer_value)


```
![Texto alternativo](https://scontent.ftij1-1.fna.fbcdn.net/v/t1.15752-9/344301214_1264726620834552_3319900546932863438_n.png?_nc_cat=110&ccb=1-7&_nc_sid=ae9488&_nc_ohc=_06ySVvvLJ4AX-l0-vd&_nc_ht=scontent.ftij1-1.fna&oh=03_AdSGw1HjAWfefChq4z0SGgbPURZDRsS6QRqTgzXbcJms6Q&oe=648918F5)
