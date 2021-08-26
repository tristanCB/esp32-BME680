# micropython ESP32 environmental data logger
> Simple device to log environmental conditions. It uses limited amount of persistent flash memory ~0.5 Mb to store temperature, pressure and relative humidity and gas conductivity as measured by multiple BME680 digital sensors (BOSCH sensortech).

## Example
                                        ┌────────────────┐    ┌────────────────┐
                                        │BME680          │    │BME680          │
                                        │                │ ,  │                │  ...
                                        │Vin+┼Gnd┼SCL┼SDA│    │Vin+┼Gnd┼SCL┼SDA│
                                        │   │   │   │            │   │   │   │
                                        ├──.│. .│. .│.───────────┘   │   │   │
                                        │   │   │   │                │   │   │   
                                        │   ├──.│. .│. ──────────────┘   │   │
                ┌────────┐              │   │   │   │                    │   │
                │~9-24V  │  5v+      ┌──▼───▼───▼───▼───────┐            ▼   ▼
    Vin+ ──────►│ Step   ├──────────►│ESP32     I2C Bus 1   │          I2C Bus 2
                │  down  │   v-      │                      │
    Vin-───────►│ Conv.  ├──────────►│                      │
                │        │           │                      │
                │        │           │ Wifi: MyESP32        │
                │        │           │ Pass: elderberry     │
                └────────┘           └──────────────────────┘

### Workflow
1. Connect to ESP32's wifi network then microcontroller using webrepl
2. ... or connect direct via serial port (ex. using PuTTy)
3. Send empty data.txt using webrepl or ampy. 
4. Reset (power cycle or reset button).
5. Let log for a given period...
6. Get data.txt suing weprepl or ampy.
7. Enjoy data!
8. Recharge battery and repeat.

### Notes
1. https://github.com/micropython/webrepl
1. https://docs.micropython.org/en/latest/esp32/quickref.html
1. https://github.com/pimoroni/bme680-python
1. https://github.com/scientifichackers/ampy 
1. https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/
1. https://www.espressif.com/en/products/socs/esp32