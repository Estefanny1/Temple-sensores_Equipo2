
 # SENSOR KY-025
 ## CODIGO  

```Python
from machine import Pin
import time

ReedSensor = Pin(18, Pin.IN)
while True:
    value = ReedSensor.value()
    print(value, end = " ")
    if value == 0:
        print("A magnetic field")
    else:
        print("There is no magnetic field")
    time.sleep(0.1)

 ```
 
 
 
![sen25](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/dda95bac-bd62-4bd0-a00d-9011e7ccb64f)
![Captura de pantalla 2023-05-24 215647](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/56738af3-684e-4210-b1fe-11f353246de3)
