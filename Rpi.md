* To enable SSH, create a file named `ssh` in the `boot` directory

* The current hostname can be obtained by the command `hostname`. The default hostname is `raspberrypi` and is reachable at `raspberrypi.local`. To change the hostname, edit `/etc/hosts` file as well as `/etc/hostname` and reboot.
* Default username is `pi` and password is `raspberry`
* ##### Connecting to a wifi network: 
  Edit `/etc/wpa_supplicant/wpa_supplicant.conf` as follows
```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
 ssid="YOURSSID"
 scan_ssid=1
 psk="YOURPASSWORD"
 key_mgmt=WPA-PSK
}
```

#### Static IP configuration: 
[Difference between both ](https://raspberrypi.stackexchange.com/questions/39785/differences-between-etc-dhcpcd-conf-and-etc-network-interfaces)
* Method 1: edit `/etc/dhcpcd.conf`
```
interface wlan0
static ip_address=192.168.1.10/24
static routers=192.168.1.1
static domain_name_servers=8.8.8.8
```
* Method 2:  edit ` /etc/network/interfaces`
```
allow-hotplug usb0
iface usb0 inet static
        address 192.168.7.2
        netmask 255.255.255.0
        network 192.168.7.0
        broadcast 192.168.7.255
        gateway 192.168.7.1
```
#### Rpi as USB - Ethernet device 
[List of ther usb devices -  serial, mass storage etc](https://gist.github.com/achuwilson/04979ded553e7278131427335e1a4b85)
[Adafruit -  Turn Rpi into Ethernet gadget](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/ethernet-gadget)
*  Edit `boot/config.txt` and add ``dtoverlay=dwc2`` as last line.( also may have to disable `otg_mode=1` line)
* Edit `boot/cmdline.txt` and after `rootwait` (the last word on the first line) add a space and then `modules-load=dwc2,g_ether`
* Reboot
* On reboot terminal screen (if connected to HDMI/tty console cable), you can see `g_ether` device.
* The usb ethernet device will show up as `usb0`




