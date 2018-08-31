# VNC
VNC is a graphical desktop sharing system used to remotely control another computer. This can be especially useful if certain action demand GUI access to be performed.

1. Open the RealVNC Server configuration interface by clicking on the menu bar icon
2. On the VNC Server window, click the hamburger menu, and select "Options"
3. Select "Security" if not already selected and set Authentication to "VNC password"
4. Set up a "Standard user" with a password of 8 characters or less
5. Then open "Screen Sharing" on your Mac, and from the "Connection" menu select "New" and type in the IP address of your Pi i.e `raspberrypi.local`
6. When challenged, enter the password you setup at the Pi in step 4.
