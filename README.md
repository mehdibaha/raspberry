# raspberry
This repository stores configuration files, resources and how-tos for setting up and using a Raspberry Pi.

**This guide is primarily targeted to Rapsberry Pi 3 & macOS users.**

## First setup
NOOBS is an operating system installation manager for the Raspberry Pi ([available for download here](raspberrypi.org/downloads)).

### Install NOOBS
Once you've downloaded the NOOBS zip file, you'll need to copy the contents to a formatted SD card on your computer:

1. Format your SD card with [SD Card Formatter](https://www.sdcard.org/downloads/formatter_4/), select the SD card volume and under `Quick format`, type `RASPBERRYPI`.
2. Unzip & copy the extracted files onto the root directory of the SD card:

        $ unzip NOOBS_v2_8_1.zip -d NOOBS/
        $ sudo cp -R NOOBS/* /Volumes/RASPBERRYPI/

3. Eject the SD card, it's ready for its first boot.

### Install Raspbian (or other OS)
When you boot the Raspberry Pi for the first time, NOOBs asks you to choose an OS to install.

We recommend choosing Raspbian as it is the default OS pre-installed in NOOBS (also, it's really nice).

The install should take some time to complete (~30 minutes), and then you should be all set!

## Configuration
For info on how to configurate your Rasperry Pi, [checkout this guide](CONFIGURATION.md).

## Kodi
For info on how to add Kodi to your Raspberry Pi, [checkout this guide](KODI.md).

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
