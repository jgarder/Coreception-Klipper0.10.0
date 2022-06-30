# Coreception-Klipper0.10.0
 sainsmart Coreception 300  with Klipper. This will hold general installation and config

1. Get Coreception (or any robin nano printer) and setup with Bltouch in mtl detector 2 spot according to pic. 
2. get raspberryPI (LOL)
3. install OS (i chose FluiddOS which is just debian with klipper/mainsail/moonraker preinstalled)
4. copy over printer.cfg which contains all pinouts to control printer as well as macros for calibration and setup
5. setup extruder/Bed PID
6. Setup ZOffset
7. testprint
8. pressure advance
9. testprint
10. enjoy

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
