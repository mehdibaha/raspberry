# raspberry

This repository stores configuration files, resources and how-tos for setup and use of my Raspberry Model 3.

*Notice: This guide is primarily targeted to macOS users.*

## First setup

NOOBS is an operating system installation manager for the Raspberry Pi ([available for download here](raspberrypi.org/downloads)).

### Install NOOBS

Once you've downloaded the NOOBS zip file, you'll need to copy the contents to a formatted SD card on your computer:

1. Format your SD card, select the SD card volume and choose Erase with MS-DOS format
2. Copy the extracted files onto the root directory of the SD card

### Install Raspbian (or other OS)

When you boot the Raspberry Pi for the first time, NOOBs asks you to choose an OS to install.

We recommend choosing Raspbian as it is the default OS pre-installed in NOOBS (also, it's really nice).

The install should take some time to complete (~15 minutes), and then you should be all set!

## Configuration

After installation of Raspbian, shutdown the Raspberry, and plug the SD card in your computer.

### 1. Enable WIFI access

Fill the following file:

    sudo nano /Volumes/boot/wpa_supplicant.conf

With the contents:

    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    network={
        ssid="your-wireless-name"
        psk="your-wireless-password"
        key_mgmt=WPA-PSK
    }

### 2. Enable SSH access

Create empty `ssh` file at root of boot folder:

    sudo touch /Volumes/boot/ssh

You can also add raspberry host to your `~/.ssh/config` for convenience:

    Host rasp
        Hostname raspberrypi.local
        User pi

#### Passwordless SSH access
To enable key-based access, first make sure you have a public key stored in your `.ssh` folder (if you don't, generate one), then simply run:

    ssh-copy-id rasp

### 3. Raspberry Pi config

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
