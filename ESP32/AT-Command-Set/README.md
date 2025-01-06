# Introduction

[AT-Command Set](https://docs.espressif.com/projects/esp-at/en/latest/esp32/AT_Command_Set/index.html) is a stand alone firmware running on ESP32. With serial AT-Commands on UART Pins 16, 17 you can set the esp32 module to various modes e.g. to connect to a wifi or connect to a MQTT-Broker and many more...

# Set Up
How to compile the AT-firmware by yourself? Please refer to Compile ESP-AT Project Locally ON LINUX description below.

read this, but not all hints are must do  
[Compile ESP-AT Project Locally](https://docs.espressif.com/projects/esp-at/en/latest/esp32/Compile_and_Develop/How_to_clone_project_and_compile_it.html)  
[Get Started](https://docs.espressif.com/projects/esp-idf/en/release-v5.0/esp32/get-started/index.html)  
[Standard Toolchain Setup for Linux and macOS](https://docs.espressif.com/projects/esp-idf/en/release-v5.0/esp32/get-started/linux-macos-setup.html)  

navigat to some dir of your chios and do a git clone  
`git clone --recursive https://github.com/espressif/esp-at.git`  

Make sure python command will work. There ar issues with python vs. python3 (alias). To be sure reinstall python3 as native, system wide python with.  
[install python](https://askubuntu.com/questions/320996/how-to-make-python-program-command-execute-python-3)  
`sudo apt install python-is-python3`  

To be sure all recommended ptyhon packages are installed run  
`sudo apt-get install git wget flex bison gperf python3 python3-pip python3-venv cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0`

In terminal navigate to the cloned local repo and do  
`./build.py install`
this will clone/download the esp-idf toolchain (and dependencies if needed) in the same dir as esp-at. It takes some time!  
The installer will ask for some parameters like `esp32` as device, `esp32-wroom` as module and `silent mode off`.  

Then run  
`./build.py build` to check everything is working.  

Then wire up the ESP32 Board on to a TTL-USB Converter dongle and use the flash commend  
`./build.py -p /dev/ttyUSB0 flash`

use  
`./build.py menuconfig` to enable/disable features according to esp32 hardware capability (BLE, webserver mode, ...) and build again.  