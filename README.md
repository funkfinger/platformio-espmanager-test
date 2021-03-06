# Platformio ESPmanager

trying to combine: [Platformio](https://github.com/platformio/platformio), [ESPmanager](https://github.com/sticilface/ESPmanager) and [Arduino ESP8266 - release candidate because ESPmanger is using that](https://github.com/esp8266/Arduino/tree/2.1.0-rc2)

In order to get Platformio to build a project based on ESP8266 release candidate, I had to do the following - [basically these instructions](https://github.com/platformio/platformio/issues/401#issuecomment-166958952):

- replaced `~/.platformio/packages/framework-arduinoespressif` files with those downloaded zip of the [ESP8266 Arduino RC](https://github.com/esp8266/Arduino/archive/2.1.0-rc2.zip) - if the `framework-arduinoespressif` folder isn't there, try building the project.
- replaced `~/.platformio/packages/ldscripts` with [these files]( https://github.com/platformio/platformio-pkg-ldscripts/tree/esp8266_stage)

I think I can get back to norm by doing a- though the `ldscripts` folder will still be messed up...

    platformio platforms uninstall espressif
    platformio platforms install espressif
    
Wondering if I could use the following to set these as seen in the [repo](https://github.com/platformio/platformio-pkg-ldscripts/tree/esp8266_stage) :

    [env:specific_ld_script]
    build_flags = -Wl,-Tname_of_script.ld