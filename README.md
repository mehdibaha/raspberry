# raspberry

This repository stores configuration files, resources and how-tos for setup and use of my Raspberry Model 3.

*Notice: This guide is primarily targeted to macOS users.*

## First setup

New Out Of Box Software (NOOBS) is an easy operating system installation manager for the Raspberry Pi. It is available for download on the [Raspberry Pi website](raspberrypi.org/downloads).

### How to install NOOBS on an SD card

Once you've downloaded the NOOBS zip file, you'll need to copy the contents to a formatted SD card on your computer:

1. Format your SD card, select the SD card volume and choose Erase with MS-DOS format
2. Copy the extracted files onto the root directory of the SD card

### First boot

When you boot the Raspberry Pi for the first time, you're asked to choose an OS.

We recommend choosing Raspbian as it is the default OS pre-installed in NOOBS (also, it's really nice).

## Configuration

Plug your SD card

### Enable WIFI access

Fill the following file

    sudo nano /Volumes/boot/wpa_supplicant.conf

With the contents:

    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=FR

    network={
        ssid="your-wireless-name"
        psk="your-wireless-password"
        key_mgmt=WPA-PSK
        proto=WPA
    }

### Enable SSH access

    sudo touch /<sd mount point>/boot/ssh

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
