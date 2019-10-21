# RaspberryPi-Headless
# Installation of the SD card
## Installation of Raspbian OS
You will need 
* Micro SD card
* Micro SD card reader 
* [Git bash](https://gitforwindows.org/) if on Windows

To do so follow these steps:

1. Download the latest version of [Raspbian](https://www.raspberrypi.org/downloads/raspbian/). Raspbian Buster with desktop and recommended software is the safest way to go now 
2. Download and install a software like [RUFUS](https://rufus.ie/) or [balenaEtcher](https://www.balena.io/etcher/)
3. Unzip Raspbian and prepare your SD card. Make sure that there is nothing critical on the SD card as it will be formatted
4. Use the etcher to make the SD card bootable with Raspbian on it

If you insert the SD card into the raspberry pi and power it. The system should boot up normally.

## Setup a wireless connection without mouse and keyboard

If you want to connect to the raspberry pi without using any mouse and keyboard setup a good way is to do it with another PC connected on the same network. 
In order to do so, a SSH connection needs to be done between the pi and the PC. The pi will need to have a proper internet connection to the same network as the PC and SSH enable.

All these things can be done quite easily in Raspbian itself but doing without any access to the pi mouse and keyboard could be challenging.

### Adding the Wi-Fi connection

1. Insert the SD card on you PC
2. Use a good tool like [Notepad++](https://notepad-plus-plus.org/) to edit files
3. The SD card should be named "boot". Into this `boot` drive, create a file called `wpa_supplicant.conf` using Notepad. Make sure that the extension is `conf` and not `conf.txt`
4. Write this into the file and change to match your Wi-Fi SSID and password:
```
country=CH # Your 2-digit country code
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
network={
    ssid="YOUR_NETWORK_NAME"
    psk="YOUR_PASSWORD"
    key_mgmt=WPA-PSK
}
```

### Enable SSH 

You will need to have [Git bash](https://gitforwindows.org/) installed on windows or using the terminal on Mac

1. Insert the SD card on you PC
2. Go with the console to the `boot` drive. 
On Git bash: `cd /THE_LETTER_OF_THE_BOOT_DRIVE`
On Mac: `cd /Volumes/boot`
3. Write down `touch ssh`

This should create an empty file called `ssh` without any extension attached. The system will recognize this on boot up and activated SSH for you.

Now that you have everything setup, the SD card can go into the pi and the pi should powers up and connect to the internet.

## Connecting to the Raspberry pi
Connecting with SSH is really handy you can do so by using a SSH client like [Putty](https://www.putty.org/).

In Putty use the raspberry pi local IP address to connect to it. Then the default user is `pi` and the password `raspberry`. Make sure to change those if the pi goes into production environment.

## Sources
[How to Set up Wi-Fi on Your Raspberry Pi Without a Monitor](https://howchoo.com/g/ndy1zte2yjn/how-to-set-up-wifi-on-your-raspberry-pi-without-ethernet)


[How to Enable SSH on Raspberry Pi Without a Screen](https://howchoo.com/g/ote0ywmzywj/how-to-enable-ssh-on-raspbian-without-a-screen)
