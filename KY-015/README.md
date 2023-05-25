
 # SENSOR KY-015
 ## CODIGO  
```
 import dht12
import machine
import time
import ssd1306


sda_pin = machine.Pin(4) # GPIO4 como SDA
scl_pin = machine.Pin(5) # GPIO5 como SCL
i2c = machine.I2C(-1, sda=sda_pin, scl=scl_pin)
oled = ssd1306.SSD1306_I2C(128, 32, i2c)


dht_pin = machine.Pin(12, machine.Pin.IN, machine.Pin.PULL_UP) # GPIO12 como entrada
dht_sensor = dht12.DHT12(dht_pin)

while True:
    
    dht_sensor.measure()
    temp = dht_sensor.temperature()
    hum = dht_sensor.humidity()
    
    
    oled.fill(0)
    oled.text("TEMP: {:.1f} C".format(temp), 0, 0)
    oled.text("HUM: {:.1f} %".format(hum), 0, 10)
    oled.show()
    
    time.sleep(2) # Espera 2 segundos antes de la próxima lectura

 ```

 
