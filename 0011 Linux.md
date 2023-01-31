- [Navigate directores faster with bash](https://mhoffman.github.io/2015/05/21/how-to-navigate-directories-with-the-shell.html)

- free space by removing old versions of packages installed using snapd
```
#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu

LANG=en_US.UTF-8 snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done

```


Mirror IPad/IPhone screen on linux similar to AirPlay-  use UXPlay https://github.com/antimof/UxPlay. Same thing on RPi, using RPi libraries - RPiPlay https://github.com/FD-/RPiPlay


[Magic Wormhole](https://github.com/magic-wormhole/magic-wormhole) - This package provides a library and a command-line tool named wormhole, which makes it possible to get arbitrary-sized files and directories (or short pieces of text) from one computer to another. The two endpoints are identified by using identical "wormhole codes"


youtube-dl  download audio only 
`youtube-dl -i --extract-audio --audio-format mp3 --audio-quality 0 YT_URL`

pdf reader https://github.com/ahrm/sioyek/releases

Speed up sklearn using Intel libraries https://intel.github.io/scikit-learn-intelex/

Install opencv4 for python2 in ubuntu 20.04
``````python 
pip2 install opencv-python==4.2.0.32
``````

Change Geolocation firefox

https://www.googleapis.com/geolocation/v1/geolocate?key=%GOOGLE_LOCATION_SERVICE_API_KEY%

Go to about:config.

Type in geo.provider.network.url (or geo.wifi.uri in older versions)

Change the value to something like this:

NYC:
data:application/json,{"location": {"lat": 40.7590, "lng": -73.9845}, "accuracy": 27000.0}


[Reduce the large size of PDFs](https://leancrew.com/all-this/2022/01/reducing-the-size-of-large-pdfs/)


#### LCD touch screen along with normal screen on ubuntu - set touch events to particular screen only
		
```
xinput map-to-output device output

```

device : input device ID obtained using xinput command
output : DISPLAY ID obtained using xrandr command

example: 
```
xinput map-to-output 13 DP-5
```





#### Set LCD screen brightness.

```
sudo ddccontrol dev:/dev/i2c-7 -r 0x10 -w 20
```

0x10 -  address of the brightness register, use ddccontrol -p to probe



#### PC motherboard beep in Ubuntu
add yourself (the user) to input users group

```
sudo usermod -aG input USERNAME

```
Change  device permission if needed
```
sudo chmod 777 /dev/input/by-path/platform-pcspkr-event-spkr

```


edit the `/etc/modprobe.d/blacklist.conf` file (using gksudo gedit perhaps) and comment out line that says `blacklist pcspkr` and then restart or `sudo modprobe pcspkr`

use the beep program to generate beep


##### Launch GSConnect from command line in i3wm
You could start it with `gapplication`:
````
gapplication launch org.gnome.Shell.Extensions.GSConnect
````
But you'd have to get the [.desktop file](https://github.com/andyholmes/gnome-shell-extension-gsconnect/blob/master/data/org.gnome.Shell.Extensions.GSConnect.desktop) installed first; usually the shell extension installs it on first run. You could then open the settings and use it as a crude interface with:
````
gapplication action org.gnome.Shell.Extensions.GSConnect settings
````

#### Task manager with Pomodoro timer
https://github.com/johannesjo/super-productivity


### Bluetooth Audio
SONY bluetooth headset Device 74:45:CE:95:3F:02 WI-XB400
use the `bluetoothctl` to connect and manage bluetooth devices using the following commands.( had good autocomplete features too)
```
bluetoothctl paired-devices
bluetoothctl
power on
agent on 
scan on 
scan off

connect 74:45:CE:95:3F:02
```

also `bt-device -l`


#### Pulseaudio Settings 

[Enable High Quality Audio on Linux](https://medium.com/@gamunu/enable-high-quality-audio-on-linux-6f16f3fe7e1f)

`/etc/pulse/daemon.conf`

```

default-sample-format = float32le  
default-sample-rate = 48000  
alternate-sample-rate = 44100  
default-sample-channels = 2  
default-channel-map = front-left,front-right  
default-fragments = 2  
default-fragment-size-msec = 125  
resample-method = soxr-vhq   
high-priority = yes  
nice-level = -11  
realtime-scheduling = yes  
realtime-priority = 9  
rlimit-rtprio = 9  
daemonize = no
```

also check `/etc/pulse/default.pa`


Audio levels and devices  `pavucontrol`


Check if pulseaudio is running ` pulseaudio --check` It normally prints no output, just exit code. 0 means running.
Restart Pulseaudio  - `pulseaudio -k`
Start pulseaudio as daemon `pulseaudio -D`


#### clock in terminal  
`tty-clock`

### i3WM Settings
`.config/i3/config`
`.config/i3/i3status.conf`


### Apps
 RSS Reader - Fluent
 Image Viewer -  qimgv (https://github.com/easymodo/qimgv)
								(gwenview)




Getting JoySTick / Gamepad events in python  - https://github.com/piborg/Gamepad