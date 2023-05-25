# Sensor KY-001 18B20 TEMP
El sensor de temperatura KY-001 se programo para recibir la temperatura actual y su conexion, solo se ocupan las librerias para detectar la temperatura.

# Codigo
```python
import machine
import onewire
import ds18x20
# Declaración del pin de entrada que está conectado con el módulo del sensor
KY001_Signal_PIN = 4
# Configuración de las bibliotecas
oneWire = onewire.OneWire(machine.Pin(KY001_Signal_PIN)) # Crear un objeto OneWire utilizando el pin de entrada
sensors = ds18x20.DS18X20(oneWire) # Crear un objeto DS18X20 utilizando el objeto OneWire
# Inicialización de la salida serial
uart = machine.UART(0, 9600)
print("KY-001 medición de temperatura")
# Inicialización del sensor
roms = sensors.scan() # Escanear los dispositivos conectados al bus OneWire
sensors.convert_temp() # Iniciar la conversión de temperatura en el sensor
# Bucle principal del programa
while True:
    # Iniciar la medición de temperatura...
    sensors.convert_temp()
    machine.delay(750)
    # ... y mostrar la temperatura medida
    for rom in roms:
        temp = sensors.read_temp(rom)
        print("Temperatura: ", temp, "C")
    machine.delay(1000) # Esperar 1 segundo antes de la siguiente medición
```
