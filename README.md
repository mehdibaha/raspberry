# raspberry

This repository stores configuration files, resources and how-tos for setup and use of my Raspberry Model 3.

*Notice: This guide is primarily targeted to macOS users.*

## I. First setup

NOOBS is an operating system installation manager for the Raspberry Pi ([available for download here](raspberrypi.org/downloads)).

### 1. Install NOOBS

Once you've downloaded the NOOBS zip file, you'll need to copy the contents to a formatted SD card on your computer:

1. Format your SD card with [SD Card Formatter](https://www.sdcard.org/downloads/formatter_4/), select the SD card volume and choose `Quick format` under the name `RASPBERRYPI`.
2. Unzip & copy the extracted files onto the root directory of the SD card:

        $ unzip NOOBS_v2_8_1.zip -d NOOBS/
        $ sudo cp -R NOOBS/* /Volumes/RASPBERRYPI/

3. Eject the SD card, it's ready for the first boot!

### 2. Install Raspbian (or other OS)

When you boot the Raspberry Pi for the first time, NOOBs asks you to choose an OS to install.

We recommend choosing Raspbian as it is the default OS pre-installed in NOOBS (also, it's really nice).

The install should take some time to complete (~30 minutes), and then you should be all set!

## II. Configuration

After installation of Raspbian, shutdown the Raspberry, and plug the SD card in your computer.

### 1. Enable WIFI access

Fill the following file:

    $ sudo nano /Volumes/boot/wpa_supplicant.conf

With the content:

    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    network={
        ssid="your-wireless-name"
        psk="your-wireless-password"
        key_mgmt=WPA-PSK
        priority=1
        id_str="home"
    }

### 2. Enable SSH access

Create empty `ssh` file at root of boot folder:

    $ sudo touch /Volumes/boot/ssh

To add an alias for your raspberry host, add the following config to your `~/.ssh/config`:

    Host rasp
        Hostname raspberrypi.local
        User pi

### 3. Raspberry Pi config

#### Upgrade dependencies

    $ sudo apt-get update && sudo apt-get dist-upgrade -y
    $ sudo apt autoremove && sudo apt-get clean # cleanup unused dependencies

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

## III. Kodi

### 1. Configuring Your Raspberry Pi for Kodi
Kodi is media centre software which runs on Raspberry Pi.

Before you install Kodi, you’ll need to ensure your Pi is set up correctly, by setting with `raspi-config`:

* Expanding your file system (this happen automatically when booting Stretch for the first time)
* Altering memory split (64MB -> 256MB)
* Enabling video codecs (Enabling Camera)
* Setting the Right Desktop Driver (choose Original non-GL desktop driver)

### 2. Installing Kodi
To get Kodi running on Raspbian, you'll need to run:

    $ sudo apt-get install kodi -y

#### Media collection
To organize your library collection, [follow this tutorial](https://kodi.wiki/view/Adding_video_sources).

#### IPTV Simple Client
IPTV Simple PVR Client support m3u playlists, streaming of Live TV for multicast/unicast sources, listening to Radio channels and EPG.

To install the plugin in Kodi, you need to:

1. Run in the terminal: `$ sudo apt-get install kodi-pvr-iptvsimple`
2. Go to Settings -> Add-ons -> Enabled add-ons -> PVR Clients and select the IPTV Simple Client add-on
3. Select "Configure" and choose the m3u url given by your IPTV provider

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
