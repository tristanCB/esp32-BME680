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
    Vin+ ──────►│ Step   ├──────────►│ESP32     I2C Bus 1   │           I2C Bus 2
                │  down  │   v-      │                      │
    Vin-───────►│ Conv.  ├──────────►│                      │
                │        │           │                      │
                │        │           │ Wifi: MyESP32        │
                │        │           │ Pass: elderberry     │
                └────────┘           └──────────────────────┘

### Workflow
1. Connect to ESP32's wifi network
2. Webrepl micropython
3. send empty data.txt 
4. reset (power cycle or reset button)
5. let log for a given period
6. get data.txt
7. enjoy data
8. recharge battery and repeat.

### Notes
https://github.com/micropython/webrepl
https://docs.micropython.org/en/latest/esp32/quickref.html
