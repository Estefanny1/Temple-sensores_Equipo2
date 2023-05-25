 # SENSOR KY-036
 ## CODIGO  
```Python
from machine import Pin
import utime

flame_sensor = Pin(12, Pin.IN)
utime.sleep(3)

while True:
   if flame_sensor.value() == 1:
       print("Tocando")
       utime.sleep(3)
   else:
       print("null")
       utime.sleep(1)
utime.sleep(0.1)

 ```
 
![20230524_142612](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/b0dfe556-10f2-4564-b133-e0e9839fc20d)

![image](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/33fb3b1e-6e53-4535-86ed-b99573842d4e)
