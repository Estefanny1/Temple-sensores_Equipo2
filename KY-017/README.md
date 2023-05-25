 # SENSOR KY-017
 ## CODIGO  
```Python
# Valores de referencia
valor_horizontal = 0
valor_vertical = 1

while True:
    valor_actual = tilt_pin.value()
    if valor_actual == valor_horizontal:
        inclinacion_rad = math.atan2(0, -1)  # 0 radianes
        inclinacion_grados = math.degrees(inclinacion_rad)
        print("El tilt switch está en posición horizontal. Inclinación: {:.2f} grados".format(inclinacion_grados))
    elif valor_actual == valor_vertical:
        inclinacion_rad = math.atan2(1, 0)  # Pi/2 radianes
        inclinacion_grados = math.degrees(inclinacion_rad)
        print("El tilt switch está en posición vertical. Inclinación: {:.2f} grados".format(inclinacion_grados))
    else:
        print("Valor inválido del tilt switch")

    time.sleep(0.1)

 ```
 
![20230523_145427](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/71e774a1-7d5b-416a-b718-0b2cabe87211)
![sensor](https://github.com/Estefanny1/Temple-sensores_Equipo2/assets/124211869/73d9d3be-fb4b-4285-82c9-06ce5431bf6a)
