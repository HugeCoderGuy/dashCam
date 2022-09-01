# Raspberry Pi Dash Camera
Rather than buy a ordinary dash camera online, I decided to build this barbaric mess instead.
<p align="center">
<img src="https://media.giphy.com/media/Jx5bLprFNUCUhqeEbr/giphy-downsized.gif" width="500" align="center">
</p>

The above video captures the chaos of driving through Kings Beach (Tahoe) durring summer. Just in case you were wondering, this was certainly not cheaper than buying a dash camera. However it was considerably more fun.

## Features
- Video capture and saving implemented in seperate threads for improved preformance
- Memory management function that deletes 7 day old videos, double checks system memory, and will delete additional videos if system memory is less than 5GB
- Long drives greater than 30mins are seperated into 30min segments with intermittent system memory checks
  - RasPi cross checks ignition before powering down so that power cycling car doesn't prevent next video session
- Videos continue for 30s after car powers off and videos are labeled with ignition state when closing out
- Timed relay powers down RasPi after 60s to prevent unnecessary current draw from car battery
- Unplugging camera on power up prevents videos from being deleted. 

Overall, my car hasn't died on me yet and my not-so-official circuit has held up. The circuit powering the pi can be seen below.
<p align="center">
<img src="https://github.com/HugeCoderGuy/dashCam/blob/main/raw_honda_fit.jpg" width="400" align="center">
</p>

## Setup
1. Flash a 32gb or greater with the RasPi imager. I set mine up with the standarded OS.
2. Copy this repo into the home directory of your pi after you power it up and connect (headless works fine)
3. Move the dashCam.py script to your pi base directory and then edit your rc.local script by typing this in the command line:
```
sudo nano /etc/rc.local
```
4. before `exit 0`, type this with the & symbol at the end so that the pi completes boot up after the script begins to run.
```
sudo python /home/pi/dashCam.py &
```
5. Install numpy and openCV with `sudo apt install`
6. Build the circuit that is seen above with x2 voltage stepdown modules, x1 delayed relay, a microusb plug with flying leads, and x2 fuse taps
7. Plug the microUSB into the microUSB port, the usb camera into a usb port, and the 3.3V/Grnd wires into GPIO 21 and Grnd which are located closest to the USB ports of the pi:
<p align="center">
<img src="https://docs.microsoft.com/en-us/windows/iot-core/media/pinmappingsrpi/rp2_pinout.png" width="400" align="center">
</p>

### Code can be found [here!](https://github.com/HugeCoderGuy/dashCam/blob/main/dashCam.py)
