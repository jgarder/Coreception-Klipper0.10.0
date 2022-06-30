# Coreception-Klipper0.10.0
 sainsmart Coreception 300  with Klipper. This will hold general installation and config

1. Get Coreception (or any robin nano printer) and setup with Bltouch in mtl detector 2 spot according to pic. 
2. get raspberryPI (LOL)
3. install OS (i chose FluiddOS which is just debian with klipper/mainsail/moonraker preinstalled)
4. compile klipper for your mcu which should be a MKS Robin Nano (v1.2.004) board on stock coreception. 
5. run "make menuconfig", setup for the mcu STM32F103, enable "extra low-level configuration setup", select the 28KiB bootloader, and serial (on USART3 PB11/PB10) communication.
6. run "make"
7. "make flash" does not work with MKS Robin,run the following command: ./scripts/update_mks_robin.py out/klipper.bin out/Robin_nano.bin Copy the file out/Robin_nano.bin to an SD card and then restart the printer with that SD card.

8. copy over printer.cfg which contains all pinouts to control printer as well as macros for calibration and setup
9. setup extruder/Bed PID
10. Setup ZOffset
11. testprint
12. pressure advance
13. testprint
14. enjoy

## some commands used to get everything setup 
sudo apt-get install git -y
cd ~/klipper/
make menuconfig
make
ls /dev/serial/by-id/*
sudo service klipper stop
cd ~
git clone https://github.com/th33xitus/kiauh.git
./kiauh/kiauh.sh
