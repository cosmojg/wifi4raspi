# wifi4raspi
These files will allow you to SSH into Arch Linux (or any other systemd-based Linux distro) on your Raspberry Pi WITHOUT ethernet cables, keyboards, or HDMI displays! All you need is your Raspberry Pi, a micro-USB power cord, a wifi dongle, an SD card, and whatever you're using to read this. Configure the files to your liking, drag and drop the entire repository into your root directory, and you're good to go.

## Step-by-Step Walthrough
1. Install Arch Linux ARM on your Raspberry Pi. (Alternatively, install a different systemd-based Linux distribution of your choice.) This is pretty simple. Follow either [this guide](https://archlinuxarm.org/platforms/armv6/raspberry-pi) or [this guide](https://github.com/phortx/Raspberry-Pi-Setup-Guide), but STOP before unmounting boot and root. Leave these mounted, and leave the SD card in your computer.

2. Replace "MYSSID" and "MYPASSPHRASE" on Line 9 of /usr/bin/wifi4raspi with your actual SSID and passphrase.

3. Copy the contents of this folder into the root of your Arch Linux ARM installation. (Alternatively, copy the individual files to their respective locations in your systemd-based Linux distribution).

4. Make sure that you are in the root directory of your Arch Linux ARM installation (you can check this by running pwd), and run the following in terminal: `sudo ln -s ./usr/lib/systemd/system/wifi4raspi.service ./etc/systemd/system/multi-user.target.wants/wifi4raspi.service`

5. Now, continue following the guides linked in Step 1, and unmount both boot and root. Remove the SD card from your computer, insert it into your Raspberry Pi, ensure that a wifi dongle is plugged into your Raspberry Pi, and connect your Raspberry Pi to a source of power using a micro-USB cable.

6. If all goes well, your Raspberry Pi should show up on your network! I recommend using the nmap utility to search for it. Bear in mind that it will probably show up under a name based upon the wifi dongle you're using. In case you missed it in the guides, root and alarm are the default accounts accessible in Arch Linux ARM. Their default passwords are root and alarm respectively. (I strongly recommend you change these ASAP, this is a frighteningly obvious security hole.)

BONUS. As this is a fairly hacky way of setting up your network, I recommend you do things right once you SSH in. Netctl is a great utility for accomplishing this, and [the Arch Wiki](https://wiki.archlinux.org/index.php/Netctl) does a great job of explaining how to do it. Once you're set up with `netctl`, run `systemctl disable wifi4raspi.service` to finish cleaning up. (This undoes the symlink you created earlier.) Feel free to take things even further and delete the wifi4raspi script and service from your system.

## Closing Remarks

Well, I hope you find this helpful! It took me hours to finally get everything working so I figured I'd share my solution with the world. If you run into any sort of trouble, go ahead and open a GitHub Issue. I'll try my best to help you ASAP!
