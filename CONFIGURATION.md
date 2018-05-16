# Configuration

Configuring correctly your Pi will go a long in insuring it is properly accessible, maintanable, and happy :).

**This guide requires Raspbian to be installed on your Raspberry Pi.**

## Enable WIFI access
Plug the SD card containing your Raspbian install on your computer, and fill the following file:

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

## Enable SSH access

Create empty `ssh` file at root of boot folder:

    $ sudo touch /Volumes/boot/ssh

To add an alias for your raspberry host, add the following config to your `~/.ssh/config`:

    Host rasp
        Hostname raspberrypi.local
        User pi

## Raspberry Pi config

### Upgrade dependencies

    $ sudo apt-get update && sudo apt-get dist-upgrade -y
    $ sudo apt autoremove && sudo apt-get clean # cleanup unused dependencies

### Remove locale warnings
To avoid seeing locale warnings on each ssh login, run:

    $ sudo sed -i '/en_US.UTF-8/s/^#//g' /etc/locale.gen # uncomment line with en_US...
    $ sudo locale-gen # regenerate locale config

### Securing your Raspberry Pi
1. Change the default Raspberry Pi password by running from your raspberry:

        $ passwd

2. Enable key-based access, by making sure you have a key stored in your `.ssh` folder, then run (from your host):

        $ ssh-copy-id rasp # or raspberrypi.local if you haven't added the alias

### raspi-config
For any extra configuration, open the configuration tool by running the following command:

    $ sudo raspi-config

### dotfiles
To install [personal dotfiles](https://github.com/mehdibaha/dotfiles), do the following

    $ git clone https://github.com/mehdibaha/dotfiles .dotfiles
    $ source .dotfiles/install.sh