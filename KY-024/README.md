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
![Captura de pantalla 2023-05-24 215945](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/6f83e714-fed8-4848-b605-83b6528feb26)
