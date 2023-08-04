# Wireless driver for 2012 MacBook Pro

> **_NOTE:_**  You will need a second computer to copy and move the specified zip archive to your 2012 MacBook Pro or use an Ethernet cable to download this archive. Most distributions have an offline installation method. In my case I have 2 USB drives, one with a distribution that i want to install and the other with this driver.

Steps:
- Clone this repository and extract the files from the archive

- Copy the extracted directory(b43) to the USB drive and then to your newly installed distribution(for example to the ```Desktop``` directory).

- Open a terminal and enter the following command to create the b43 firmware directory:

```sudo mkdir /lib/firmware/b43```

- Copy the firmware files into the folder(make sure you change the path after the ```cp``` command if you didn't use a ```'Desktop'``` folder):

```sudo cp Desktop/b43/*  /lib/firmware/b43```

- Once the files have been successfully copied, it's time to run the two ```modprobe``` commands below:

```sudo modprobe -rv b43 ```

```sudo modprobe -v b43 ```

Now you should see the wireless applet detecting the signal and the Wi-Fi option working. If not, you may need to reboot.

After each shutdown or reboot you will need to open terminal and use the last two ```modprobe``` commands to get it working.
To fix this, we need to make sure that the module is automatically loaded on boot with the following commands:

```
sudo -i
echo b43  >>  /etc/modules
exit 
```
You should be all set.

If you find that you have a conflicting blacklist, please do so:

```sudo gedit /etc/modprobe.d/blacklist.conf```

Remove the line ``` 'blacklist b43' ``` Save and close gedit.
