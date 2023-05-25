
## PRUEBA 4
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
 ## PRUEBA 5
 # SENSOR JOYSTICK KY-023
 
![348365414_102903776145097_6553385901693308597_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/717a3ebe-164f-4f94-8b28-beacc2c39914)
![346143104_1416278552528717_8067493179608268175_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/d8fd48c7-6a22-4323-ac05-0a8e904558e9)
![346141970_558720809779490_2711893195499034884_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/b42e1a3f-37af-4dbb-b594-bd262234c80b)
![346134530_128701950178092_2663836356191803617_n](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/ee88c81f-1e3e-4dfc-9dd1-e438dc1f1602)
