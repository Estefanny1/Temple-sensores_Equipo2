# SENSOR Photoresistor module KY-018
 ![348357057_243998028309667_1399446362090185094_n (1)](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/71289132/6f790ac9-e42a-4c95-8442-dae7b309f8c4)

  ## CODIGO
 ```python
from machine import ADC, Pin, I2C
from time import sleep

from machine import Pin, I2C
from ssd1306 import SSD1306_I2C

ANCHO = 128
ALTO = 64
i2c = I2C(1,scl = Pin(19), sda = Pin(18))
oled = SSD1306_I2C(ANCHO, ALTO, i2c)

photoPIN = 26

def readLight(photoGP):
    photoRes = ADC(Pin(26))
    
    light = photoRes.read_u16()
    
    light = round(light/65535*100,2)
    return light

while True:
    oled.fill(0)
    
    oled.text("light: " + str(readLight(photoPIN)) +"%",0,30)
    sleep(1) # set a delay between readings
    oled.show()
 ```
