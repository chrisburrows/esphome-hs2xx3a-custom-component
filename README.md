## This repo houses development of a custom component to support the LeapMMW HS2xx3A series of mmWave sensors, also branded as the DFRobot sen0395.

# This repo is a fork from https://github.com/hjmcnew/esphome-hs2xx3a-custom-component

This version makes some changes so that ESPHome components are only referenced using their 'id' and not their name. This allows the names to be changed however you see fit and also reduces the chance of unwanted side effects due to name clashes.

If you just want to create a sensor device using only the MMwave sensor you're probably better off using the original component linked above - it will certainly receive updates and fixes ahead if this version. If you want to combine other sensors, you may wish to use this version since at also 'namespaces' the mmwave sensor id to start with "mmwave_" again to reduce clashes in the ids.

The name of each sensor exposed to Home Assistant may be customised by setting a prefix and or suffix that is applied to each name.


### Installation:
 * Download the [leapmmw_sensor.h](https://raw.githubusercontent.com/chrisburrows/esphome-hs2xx3a-custom-component/main/leapmmw_sensor.h) file into your esphome configuration directory
 * Include the following in the YAML configuration for your ESP board:
   ```
   substitutions:
     device_name: leapmmw
 
     # This will vary based on your board
     uart_tx_pin: TX
     
     # This will vary based on your board
     uart_rx_pin: RX
     
     # This will vary based on your board
     gpio_pin: D0
     
     # (Optional) Path to the leapmmw_sensor.h file relative to your esphome configuration directory.
     # header_file: leapmmw_sensor.h

     # (Optional) Set a prefix for the sensors / configuration settings exposed to Home Assistant. Use quotes to include whitespace.
     mmwave_prefix: "MyRoom "

     # (Optional) Set a suffix for the sensors / configuration settings exposed to Home Assistant. Use quotes to include whitespace.
     mmwave_suffix: " MySuffix"
   
   packages:
     remote_package:
       url: https://github.com/chrisburrows/esphome-hs2xx3a-custom-component
       ref: main
       files: [packages/uart.yml, packages/leapmmw_sensor.yml]
       # For additional debugging replace the above line with:
       # files: [packages/uart_debug.yml, packages/leapmmw_sensor.yml]
   ```
