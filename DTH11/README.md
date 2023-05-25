## CODIGO
import dht
import machine
import ssd1306
import time

Configura el pin del sensor DHT11
pin_dht = machine.Pin(16)  


sda_pin = machine.Pin(4)  
scl_pin = machine.Pin(5)  
i2c = machine.I2C(-1, sda=sda_pin, scl=scl_pin)
display = ssd1306.SSD1306_I2C(128, 64, i2c)

 Crea una instancia del sensor DHT11
sensor = dht.DHT11(pin_dht)

while True:
    try:
        
        sensor.measure()
        temperatura = sensor.temperature()
        humedad = sensor.humidity()
        
       
        print("Temperatura: {}°C".format(temperatura))
        print("Humedad: {}%".format(humedad))
        
        
        display.fill(0)
        
        
        display.text("Temperatura:", 0, 0)
        display.text("{} C".format(temperatura), 0, 16)
        display.text("Humedad:", 0, 32)
        display.text("{}%".format(humedad), 0, 48)
        display.show()
        
    except OSError as e:
        print("Error al leer el sensor:", e)
    
    
    time.sleep(1)
 # PRUEBA 9
![images](https://github.com/tectijuana/git-fundamentos-JoseAPulido/blob/main/imagenes/20230508_145314.jpg)

![images](https://github.com/tectijuana/git-fundamentos-JoseAPulido/blob/main/imagenes/20230508_145307.jpg)
