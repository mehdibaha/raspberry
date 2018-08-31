# raspberry
This repository stores configuration files, resources and how-tos for setting up and using a Raspberry Pi (Model 3).

**This guide is primarily targeted to macOS users.**

## First setup
NOOBS is an operating system installation manager for the Raspberry Pi ([available for download here](raspberrypi.org/downloads)).

### Install NOOBS
Once you've downloaded the NOOBS zip file, you'll need to copy the contents to a formatted SD card on your computer:

1. Format your SD card with [SD Card Formatter](https://www.sdcard.org/downloads/formatter_4/), select the SD card volume and under `Quick format`, type `RASPBERRYPI`.
2. Unzip & copy the extracted files onto the root directory of the SD card:

        $ unzip NOOBS_v2_8_1.zip -d NOOBS/
        $ sudo cp -R NOOBS/* /Volumes/RASPBERRYPI/

3. Eject the SD card, it's ready for its first boot.

### Install Raspbian
When you boot the Raspberry Pi for the first time, choose Raspbian as the OS to install (it's pre-installed + really nice).

The install should take some time to complete (~30 minutes), and then you should be all set!

## Configuration
Configuring your Pi is a key part of insuring it is properly accessible and easily usable.

For info on how to configurate your Rasperry Pi, [checkout this guide](CONFIGURATION.md).

#### Remove locale warnings
To avoid seeing locale warnings on each ssh login, run:

    $ sudo sed -i '/en_US.UTF-8/s/^#//g' /etc/locale.gen # uncomment line with en_US...
    $ sudo locale-gen # regenerate locale config

#### Securing your Raspberry Pi
1. Change the default Raspberry Pi password by running from your raspberry:

        $ passwd

2. Enable key-based access, by making sure you have a key stored in your `.ssh` folder, then run (from your host):

        $ ssh-copy-id rasp # or raspberrypi.local if you haven't added the alias

#### raspi-config
For any extra configuration, open the configuration tool by running the following command:

    $ sudo raspi-config

#### dotfiles
To install [personal dotfiles](https://github.com/mehdibaha/dotfiles), do the following

    $ git clone https://github.com/mehdibaha/dotfiles .dotfiles
    $ source .dotfiles/install.sh

### 4. Enable VNC
VNC is a graphical desktop sharing system used to remotely control another computer. This can be especially useful if certain action demand GUI access to be performed.

1. Open the RealVNC Server configuration interface by clicking on the menu bar icon
2. On the VNC Server window, click the hamburger menu, and select "Options"
3. Select "Security" if not already selected and set Authentication to "VNC password"
4. Set up a "Standard user" with a password of 8 characters or less
5. Then open "Screen Sharing" on your Mac, and from the "Connection" menu select "New" and type in the IP address of your Pi i.e `raspberrypi.local`
6. When challenged, enter the password you setup at the Pi in step 4.

## III. Kodi

### 1. Configuring Your Raspberry Pi for Kodi
Kodi is media centre software which runs on Raspberry Pi.

For info on how to add Kodi to your Raspberry Pi, [checkout this guide](KODI.md).

## Pi-hole
Pi-hole is a network-wide ad blocker via the Raspberry Pi.

For info on how to add Pi-hole to your Raspberry Pi, [checkout this guide](PI-HOLE.md).

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
