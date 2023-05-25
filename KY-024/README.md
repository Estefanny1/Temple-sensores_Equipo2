 # SENSOR KY-024
 ## CODIGO  
```Python
from machine import Pin, ADC
import time

digital = Pin(18, Pin.IN)
analog = ADC(26)

while True:
    print(str(digital.value()) + ' - ' + str(analog.read_u16()))
    time.sleep(1)

 ```
 
 
![20230523_163631](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/91f1dbf4-869c-4c22-9bff-44237391716b)
