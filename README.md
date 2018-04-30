# raspberry

This repository stores resources, configuration files and how-tos for setup and use of my Raspberry Model 3.

Notice: These guides are heavily inspired

## First setup

New Out Of Box Software (NOOBS) is an easy operating system installation manager for the Raspberry Pi.

### Download

Alternatively, NOOBS is available for download on the Raspberry Pi website: raspberrypi.org/downloads

### How to install NOOBS on an SD card

Once you've downloaded the NOOBS zip file, you'll need to copy the contents to a formatted SD card on your computer.

To 1) format your SD card, select the SD card volume and choose Erase with MS-DOS format, and then 2)copy the extracted files onto the SD card that you just formatted, so that this file is at the root directory of the SD card.

### First boot

Choose Raspbian as it is the default OS pre-installed in NOOBS (also, it's really nice), and install it.

    brew cask install osxfuse
    brew install ext4fuse
    sudo mkdir /Volumes/rpi
    sudo ext4fuse /dev/disk2s2 /Volumes/rpi -o allow_other
    sudo cp /Volumes/rpi/home/pi/Pictures/* /Users/me/work/raspi/Pix/

#### Wireless access

(To be continued)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
