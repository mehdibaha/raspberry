# Kodi

Kodi is media centre software which runs on Raspberry Pi.

**This guide requires Raspbian to be installed on your Raspberry Pi.**

## Configuring Your Raspberry Pi for Kodi

Before you install Kodi, you’ll need to ensure your Pi is set up correctly, by setting with `raspi-config`:

* Expanding your file system (this happen automatically when booting Stretch for the first time)
* Altering memory split (64MB -> 256MB)
* Enabling video codecs (Enabling Camera)
* Setting the Right Desktop Driver (choose Original non-GL desktop driver)

## Installing Kodi
To install Kodi in Raspbian, you'll need to run:

    $ sudo apt-get install kodi -y

### Media collection
To organize your library collection, [follow this tutorial](https://kodi.wiki/view/Adding_video_sources).

### IPTV Simple Client
IPTV Simple PVR Client support m3u playlists, streaming of Live TV for multicast/unicast sources, listening to Radio channels and EPG.

To install the plugin in Kodi, you need to:

1. Run in the terminal: `$ sudo apt-get install kodi-pvr-iptvsimple`
2. Go to Settings -> Add-ons -> Enabled add-ons -> PVR Clients and select the IPTV Simple Client add-on
3. Select "Configure" and choose the m3u url given by your IPTV provider
