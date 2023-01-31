### Step 1: 
Install Raspbian/Raspberry PI OS on the SD Card


### Step 2:
#### Enable SSH
Enable SSH on the raspberry Pi. Easiest way is the mount the above SD card with raspbian image on an external computer and create a file named `ssh` inside `/boot/` directory. You can use the following command from a linux/mac command line

`touch /boot/ssh`

SSH will now be enabled on next boot of R-Pi with the SD card

### Step 3:
#### Configure Rpi as USB - Ethernet device 
[List of ther usb devices -  serial, mass storage etc](https://gist.github.com/achuwilson/04979ded553e7278131427335e1a4b85)
[Adafruit -  Turn Rpi into Ethernet gadget](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/ethernet-gadget)
*  Edit `boot/config.txt` and add ``dtoverlay=dwc2`` as last line.( also may have to disable `otg_mode=1` line)
* Edit `boot/cmdline.txt` and after `rootwait` (the last word on the first line) add a space and then `modules-load=dwc2,g_ether`
* Reboot
* On reboot terminal screen (if connected to HDMI/tty console cable), you can see `g_ether` device.
* The usb ethernet device will show up as `usb0`  as a network device, if we run `ifconfig ` on R-Pi


### Step 4 :
#### IP address/ hostname settings
Connect the USB port of R-Pi ( USB port with OTG support) to the external PC.  Make sure it shows up as a ethernet network device. 

Create a new Ethernet Connection on the PC, and set IP address ( in Ipv4 tab ) as " **Link Local Only** ". You may have to disable and then enable the network connection for the changes to make effect. 

Make sure that you can ping to `raspberrypi.local`

The current hostname can be obtained by running the command `hostname` on R-Pi. The default hostname is `raspberrypi` and is reachable at `raspberrypi.local`. To change the hostname, edit `/etc/hosts` file as well as `/etc/hostname` and reboot.

If you cannot ping to `raspberrypi.local`, do the following steps to set a static IP address for the R-Pi as well as your PC and do things the conventional way.

* Plug in R-Pi SD card to an external PC
*  edit ` /etc/network/interfaces`  of R-Pi SD card and add the following
```
allow-hotplug usb0
iface usb0 inet static
        address 192.168.7.2
        netmask 255.255.255.0
        network 192.168.7.0
        broadcast 192.168.7.255
        gateway 192.168.7.1
```
* Now in your PC, create a new Ethernet Network Connection and in the IPv4 tab, create a static IP address connection with the following settings.
  ``` 
  address 192.168.7.1
  netmask 255.255.255.0
  gateway 192.168.7.1
  
	```
 * Save the connection, disable, then enable and then connect to it. Now you should be able to ping the R-Pi address (192.168.7.2 or `raspberrypi.local` )

### STEP 5 : 
#### Enable R-Pi Camera

* SSH into R-Pi
* Run `sudo raspi-config`
* Navigate to `Interfacing Options` and Enable `Camera`
* Reboot

NOTE: Do not plug in/out camera with R-Pi powered on. Always plug in camera when power cables are disconnected from R-Pi. 

### Step 6:
#### Install video streaming software on R-Pi

Note: Add an IP route on R-Pi to your external PC if you want to share internet access (to install packages). Run the following command on R-Pi

```
sudo ip route add default via xxx.xxx.xxx.xxx
```
where xxx.xxx.xxx.xxx is the IP address of your PC ( 192.168.7.1 in this case)

##### Option1 : mjpg_streamer
[mjpg-streamer Github](https://github.com/jacksonliam/mjpg-streamer)

* ```
```
sudo apt-get install cmake libjpeg8-dev
sudo apt-get install gcc g++

git clone https://github.com/jacksonliam/mjpg-streamer.git
cd mjpg-streamer/mjpg-streamer-experimental

make
sudo make install


```
* Once compiled and installed, run the following from the `mjpeg-streamer-experimental` folder to start streaming:

```
export LD_LIBRARY_PATH=.
./mjpg_streamer -o "output_http.so -w ./www" -i "input_raspicam.so"
``` 
The default port is 8080, which can be changed with the `-p 8090` argument 

You can specify options, like in raspivid:

```
export LD_LIBRARY_PATH=.
./mjpg_streamer -o "output_http.so -w ./www" -i "input_raspicam.so -x 1280 -y 720 -fps 15 -ex night"
```

It does support upto 1080p 30fps, but the bandwidth produced would be more than the usb bus (and therefore ethernet port / wifi dongle) can provide. 720p 15fps is a good compromise.

Here's some help for this input plugin:

```
 ---------------------------------------------------------------
 Help for input plugin..: raspicam input plugin
 ---------------------------------------------------------------
 The following parameters can be passed to this plugin:

 [-fps | --framerate]...: set video framerate, default 5 frame/sec
 [-x | --width ]........: width of frame capture, default 640
 [-y | --height]........: height of frame capture, default 480
 [-quality].............: set JPEG quality 0-100, default 85
 [-usestills]...........: uses stills mode instead of video mode
 [-preview].............: enable full screen preview
 
 -sh : Set image sharpness (-100 to 100)
 -co : Set image contrast (-100 to 100)
 -br : Set image brightness (0 to 100)
 -sa : Set image saturation (-100 to 100)
 -ISO : Set capture ISO
 -vs : Turn on video stabilisation
 -ev : Set EV compensation
 -ex : Set exposure mode (see raspistill notes)
 -awb : Set AWB mode (see raspistill notes)
 -ifx : Set image effect (see raspistill notes)
 -cfx : Set colour effect (U:V)
 -mm : Set metering mode (see raspistill notes)
 -rot : Set image rotation (0-359)
-stats : Compute image stats for each picture (reduces noise)
 -drc : Dynamic range compensation level (see raspistill notes)
 -hf : Set horizontal flip
 -vf : Set vertical flip
 ---------------------------------------------------------------

```

* Once it starts streaming open the R-Pi IP address:port from the browser on PC 

##### Option 2 : uStreamer (higher performance)

Follow instructions on [uStreamer Github](https://github.com/pikvm/ustreamer). Similar to above option in mjpg-streamer

