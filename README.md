# Using Multiple PZEM-004T Devices with a Single Pair of RX/TX Pins
3 Phase Energy Monitoring using 3 PZEM 004-T and nodemcu (esp8266) 

This guide will help you set up multiple PZEM-004T devices using a single pair of RX and TX pins on a NodeMCU ESP8266 board. It uses ESPHome to communicate with the devices and send the data to Home Assistant.

### Prerequisites
* NodeMCU ESP8266 board
* One or more PZEM-004T devices
* Home Assistant installed and configured

### Schematics 
![wiring diagram](https://github.com/bnap00/PZEM-ESPHome/blob/main/pzem_bb.png)

## Assign Unique Addresses to Each PZEM-004T Device 

1. Ensure that only one PZEM-004T device is connected to the UART bus at a time.
2. Load the `change-address.yaml` file for each PZEM-004T device.
3. Set the `new_address` variable to a unique value between 0x01 and 0xF7.
4. Flash the firmware to the NodeMCU ESP8266 board and let it boot.
5. After the boot, check for a log containing `PZEM Addr set`.
6. Repeat these steps for each PZEM device.

**Suggestion**: Write down the updated address on the yellow portion of the PZEM; this will make your life much easier later.

**Suggestion**: Avoid using the `0x01` address, as new devices have that address by default. When you add new devices later, it will be much easier to manage the addresses.

## Finalizing the Setup

1. Load the code in the `power-meter.yaml` file in your ESPHome for the device.
2. Change the addresses in the configuration to match your PZEM-004T device addresses.
3. Flash the code to your NodeMCU ESP8266 or ESP32 board.
4. Enjoy detailed data on your power consumption habits through Home Assistant.

