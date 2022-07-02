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
9. [verify all printer components and tune extruder/Bed PID](https://github.com/Klipper3d/klipper/blob/master/docs/Config_checks.md) 
10. [Setup Extruder Steps (if Not Stock)](https://www.klipper3d.org/Rotation_Distance.html)
11. [Setup ZOffset/probe calibrate](https://github.com/Klipper3d/klipper/blob/master/docs/Probe_Calibrate.md)
12. testprint
13. [Setup pressure advance](https://github.com/Klipper3d/klipper/blob/master/docs/Pressure_Advance.md)
14. [setup the Rpi to ALSO be a secondary MCU for resonance testing](https://www.klipper3d.org/RPi_microcontroller.html)
14. [Check your Resonance](https://github.com/Klipper3d/klipper/blob/master/docs/Resonance_Compensation.md)
15. [Check resonance to check belt tension on coreXY machines](https://www.ifixit.com/Guide/Adding+ADXL345+Accelerometer/147745)
14. testprint
15. [setup Start and end Gcodes](https://allpro3d.com/quick-tip-start-and-end-gcode-in-klipper/)
16. enjoy

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

i ended up using spi 5 and needed these commands
dtoverlay=spi5-1cs
dtparameter=cs0_pin=12

SHAPER_CALIBRATE

~/klipper/scripts/calibrate_shaper.py /tmp/calibration_data_x*.csv -o /tmp/shaper_calibrate_x.png
~/klipper/scripts/calibrate_shaper.py /tmp/calibration_data_y*.csv -o /tmp/shaper_calibrate_y.png


##sources
1. [copied a lot from this](https://www.reddit.com/r/coreception/comments/peyx17/fluidd_config_for_klipper_guide_and_also_just/)

2. [beanisfat leaves a comment i use](https://www.reddit.com/r/coreception/comments/nhtl3p/klipper_tmc2208_config_for_stock_printer/)

3. [more config discussion inclusing making 2208 uart and coreception](https://www.reddit.com/r/coreception/comments/k619b1/klipper_on_elfcoreception/)
