# How to Reset and Burn New Bootloader on ESP32

The detailed tutorial is available on [Adafruit](https://learn.adafruit.com/adafruit-esp32-s2-feather/factory-reset)    

## Enter ROM bootloader mode

Before starting, make sure the ESP32 is connected to the COM port.
1. Press and hold the BOOT button down. 
2. Press and release the Reset button. 
3. Now you can release the BOOT button.

## The WebSerial ESPTool
1. Download [factory-reset-and-bootloader.bin](https://github.com/adafruit/Adafruit-Feather-ESP32-S2-PCB/raw/main/Factory-Reset/feather-esp32-s2-factory-reset-and-bootloader.bin)
2. Use __Chrome__ or __Edge__ visit [WebSerial ESPTool](https://adafruit.github.io/Adafruit_WebSerial_ESPTool/)
3. Press the __Connect__ button in the top right corner of the webpage and select the correct COM  port.
4. Once it is successfully connected, a toolbar will appear
![WebSerialToolBar](https://learn.adafruit.com/assets/116447 )
5. First click on __Erase__ then Upload the _factory-reset-and-bootloader.bin_ file to the first row with default offset (0x0)
6. Click on __Program__ and wait till the process complete. 
7. Hit __Rest__ on the board to launch the new bootloader. 



