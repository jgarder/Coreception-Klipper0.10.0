# Coreception-Klipper0.10.0
 sainsmart Coreception 300  with Klipper. This will hold general installation and config
0.Get Coreception (or any robin nano printer) and setup with Bltouch in mtl detector 2 spot according to pic. 
1.get raspberryPI (LOL)
2.install OS (i chose FluiddOS which is just debian with klipper/mainsail/moonraker preinstalled)
3.copy over printer.cfg which contains all pinouts to control printer as well as macros for calibration and setup
4.setup extruder/Bed PID
5.Setup ZOffset
6.testprint
7.pressure advance
8.testprint

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
