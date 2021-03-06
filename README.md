# Master Branch Updates for 05/16/2015
For those using PiPass 1.3 or PiPass 1.4, please use PiPass Update to receive the following updates:

 * PiPass now features a logging system that is accessible through the dashboard.
 * piPass.py works with the logging system to diagnose issues. e.g., hostapd WiFi drivers.
 * Scrollable modals.
 * PiPass form validation PHP messages now conforms to responsive design and the user interface.
 * The PiPass version can now be viewed through the dashboard.
 * Changelogs are accessible through 'About PiPass' in the dashboard.
 * The dashboard only refreshes the 'Spoofing Status' table, instead of the entire page.
 * Removed automatic refresh of the 'Show Current' page. Not really necessary.
 * Minor rewording.

Those who are on older versions can either manually update or use the pre-made PiPass 1.4 image and run PiPass Update after installation.

# PiPass - Nintendo 3DS Homepass for the Raspberry Pi
PiPass turns your Raspberry Pi into a Nintendo 3DS Homepass Relay Station. The PiPass Dashboard can be accessed through a computer or mobile device. It can manage features without the need of opening up any files manually. However, some fine-tuning may require getting your hands 'dirty'. Though the process is relatively fast and easy.

This does not showcase a complete list of features, but it gives a sense in what PiPass looks like: <a href="https://www.youtube.com/watch?v=ttoDlpEBqBU" target="_blank">PiPass Video Overview</a>.
    
# What's New in Version 1.4
PiPass 1.4 focuses on customization by empowering the dashboard with methods to do so. The goal was to minimize or completely remove the need to remote in your Raspberry Pi. This version also includes polish to the user interface and generally tightens up the dashboard into a visually appealing and smooth user interaction. The following changes were implemented in this version:

  * The PiPass Dashboard can now be used to add authenticated Nintendo 3DS systems. A wireless access point should have some form of security and by implementing an interface for this, performing this step is very easy. Please note that you should enter each MAC address on a separate line and in the format of XX:XX:XX:XX:XX:XX.
  * The PiPass Dashboard went all modals. Prompt boxes now conform to the general theme of PiPass and just makes using PiPass more pleasant and seamless.
  * General user interface improvements to descriptions and more helpful information regarding the project.
  * PiPass Settings and PiPass Update have been improved to be smarter and more helpful in case of incorrect actions.
  * <b>ADVANCED USERS:</b> The PiPass Dashboard can now be configured to use a different installation path in case there are those who use a different directory structure or another web server.

# Known Behaviours
PiPass sometimes does not display expected or up-to-date values. Chrome is known to be finicky with this and will NOT cause issues with PiPass. When in doubt, manually refresh your browser. This is related to browser caching and users have not reported any caching issues with Safari and Internet Explorer.

# Helpful Information
<b>Switching WiFi Dongles</b>

For those who like switching between different WiFi dongles, PiPass assumes that your main WiFi dongle is wlan0. I thought about making this name configurable, but I believe the Raspberry Pi should have a relatively clean list of WiFi dongles that are actually being used. If you will be switching between different WiFi dongles on the same installation of PiPass, it is recommended that you run the following command on your Raspberry Pi:

    ->  rm /etc/udev/rules.d/70-persistent-net.rules

I could make PiPass do this automatically, but it is a command that should not be ran consistently and to be only used when troubleshooting. A good use case for this would be that you tried using a incompatible WiFi dongle and then moved onto a WiFi dongle that was compatible. Between this transition, it would be good to run this command and restart your Raspberry Pi with your new WiFi dongle plugged in.

<b>RTL8188CUS Chipset</b>

Many people have been trying to get the RTL8188CUS chipset to work with PiPass. To my understanding, RTL8188CUS is problematic with Homepass in general. That means that the RTL8188CUS chipset has problems with other Homepass solutions. There are guides that help you make a RTL8188CUS chipset into an access point, but it just falls short in getting Homepass to work. 

If others have successfully gotten the RTL8188CUS chipset to work, please let me know because I do not own this chipset to help others troubleshoot.

# Testing Environment
Development and testing was done using all the components from the Canakit Raspberry Pi 2 Complete Starter Kit with WiFi. A -=new=- Nintendo 3DS XL with the 9.7.0-25U firmware was used to verify functionality of 'Homepass'.

PiPass has drivers pre-installed for Ralink, ZyDAS ZD1211/1211B, and Atheros AR5007UG chipsets. The WiFi chipset that I tested on was the Ralink RT5370. These chipsets were tested to be working for 'Homepass', so I've loaded the drivers for these other chipsets as well.

# Installation
PiPass can be installed by downloading a pre-made image for your Raspberry Pi 2 or by downloading the source files here on GitHub and setting it up manually. Manual setup will be more work, but it has the advantage of being able to use PiPass on most Linux based operating systems that are not just limited to the Raspberry Pi.

<b>PiPass Premade Image</b>

PiPass can be downloaded through these mirrors:

* <a href="https://drive.google.com/folderview?id=0B8bbfqFbkJvVfk55dzhwWUZNUkNpQ2lXMHk3bnZXOUl5V2FlOTZqX2RmZE9OQWZQOEJZYjA&usp=sharing" target="_blank">Mirror 1 @ Google Drive</a>.
* <a href="https://www.dropbox.com/sh/91rdhi212d1vqnj/AADKzZCSQg89t68nU5R_quu9a?dl=0" target="_blank">Mirror 2 @ Dropbox</a>.

The PiPass image was built using <a href="https://minibianpi.wordpress.com/" target="_blank">Minibian</a>, a light weight image based on the Raspbian operating system. The smallest SD card at my availability was 4GB, so a 4GB SD card will be required at minimum. The actual "real" size of everything is just a little over 500MB.

If you are not sure on how to install an image onto your SD card, the following guide here does an excellent job in explaining how to do this for all three major platforms:
* <a href="http://www.raspberrypi.org/documentation/installation/installing-images/" target="_blank">Installing Images</a>.

Once you have the PiPass image onto your SD card, you can now load PiPass into your Raspberry Pi. Though this is not necessary, if you need to log into your Raspberry Pi, the following guide is good if you will be accessing remotely through another computer:
* <a href="http://www.raspberrypi.org/documentation/remote-access/ssh/README.md" target="_blank">Using SSH</a>.
* <a href="http://www.raspberrypi.org/documentation/troubleshooting/hardware/networking/ip-address.md" target="_blank">Finding Your IP Address</a>.

Root access is only configured and the username and password is:

    +   Username:   root
    +   Password:   PiPass

For security sake, PiPass will only work on the Nintendo 3DS systems that you authorize. Access the PiPass Dashboard by opening up a web browser on a device of your choice and enter your Raspberry Pi's IP address into the address bar. The PiPass Dashboard should be displayed. Go to your Nintendo 3DS and open up your connection settings to find out your 3DS' MAC address. Once you have your MAC address, you can add it to the authenticated list by doing the following:

    +   Click "PiPass".
    +   Click "Settings".
    +   Enter your 3DS' MAC address on a separate line and in the format of XX:XX:XX:XX:XX:XX.
    +   Click "Save".

The PiPass image uses your router's DHCP to handle the networking aspect. If you want to make sure your installation is working, run the following command in your Raspberry Pi's terminal:

    ->  service hostapd status

Generally speaking, if hostapd services are running, you should be OK. If you have a mobile device or a computer with WiFi, check to see any available networks. If the SSID of "attwifi" or "NZ@McD1" show up, you are in luck. If both these things look good, your 3DS could have some StreetPasses already.

If things don't look good, there could be some issues with your WiFi driver. PiPass has drivers pre-installed for Ralink, ZyDAS ZD1211/1211B, and Atheros AR5007UG chipsets. Check to see if your WiFi adapter is based on one of these chipsets and make sure that it can function as an "Access Point".

If problems persist, refer to the manual guide down below for some extra help. If it is a driver problem, there might be some changes that you will need to do. I've tried to make these changes easy, so if it is a driver issue, you may want to use the PiPass Dashboard to configure the correct driver:

    +   Navigate to the PiPass Dashboard with your web browser.
    +   Click "PiPass".
    +   Click "Settings".
    +   Enter the correct driver name for "Hostapd Driver".
    +   Click "Save".

<b>Manually Installing PiPass</b>

Before you begin, there is a great guide that explains in detail on how to setup a Homepass Relay Station. It is a good read and I encourage everyone to take a look at it. It is especially helpful to those who are having WiFi driver issues. The guide, written by Semperverus, can be found <a href="https://docs.google.com/document/d/1EvmIwTIjPva5MHSFEIN0qsHtRmdRRiX3WNHu_ThxnOs/edit" target="_blank">here</a>. The following instructions will assume you are familiar with Linux and will briefly explain where everything is.

Here is a list of dependencies needed for PiPass, so install the following packages through these commands:

    ->  sudo apt-get install python -y
    ->  sudo apt-get install apache2 -y
    ->  sudo apt-get install php5 -y
    ->  sudo apt-get install hostapd -y
    ->  sudo apt-get install bridge-utils -y
    ->  sudo apt-get install p7zip-full -y

Download PiPass from the 1.4 branch as a zip file and extract the contents on your local machine. You will notice three directories inside PiPass: etc, opt, and var. These three directories are the locations where you want to install PiPass (e.g., Linux root locations would be /etc/, /opt/, and /var/). Go ahead and merge the directories and it will be safe to overwrite the files with PiPass' configuration files.

For security sake, PiPass will only work on the Nintendo 3DS systems that you authorize. Access the PiPass Dashboard by opening up a web browser on a device of your choice and enter your Raspberry Pi's IP address into the address bar. The PiPass Dashboard should be displayed. Go to your Nintendo 3DS and open up your connection settings to find out your 3DS' MAC address. Once you have your MAC address, you can add it to the authenticated list by doing the following:

    +   Click "PiPass".
    +   Click "Settings".
    +   Enter your 3DS' MAC address on a separate line and in the format of XX:XX:XX:XX:XX:XX.
    +   Click "Save".

Likewise, you can add the MAC address of your Nintendo 3DS by entering the following command:

    ->  sudo nano /etc/hostapd/mac_accept
    
Like the dashboard, each MAC address should be on a new line.

Most of the features controlled by PiPass can actually be ran through the PiPass Dashboard. Since your Raspberry Pi will act as a web server as well, you will need to make sure it has the permissions to do so. The following commands can grant execution:

    ->  sudo chmod -R 755 /var/www/
    ->  sudo chmod -R 755 /opt/PiPass/

Now this part is a little more involved as we will need to grant the Dashboard some rights for execution. Typically, you would not want to do this on a public webpage, but since PiPass is ran locally and that we have some security measures in place, it should be fine. We'll need root access, so run the following commands:

    ->  su
    ->  visudo -f /etc/sudoers
    
Now add the following line at the end of the file:

    +   www-data ALL=(ALL:ALL) NOPASSWD: ALL
    
If you are experiencing WiFi driver problems, there might be some changes that you will need to do. I've tried to make these changes easy, so if it is a driver issue, you may want to use the PiPass Dashboard to configure the correct driver:

    +   Navigate to the PiPass Dashboard with your web browser.
    +   Click "PiPass".
    +   Click "Settings".
    +   Enter the correct driver name for "Hostapd Driver".

Semperverus' guide is a excellent resource for troubleshooting. With luck, you should have PiPass working manually.

# Using PiPass

<b>The PiPass Dashboard</b>

The PiPass Dashboard can be accessed on a device on your network by typing in your Raspberry Pi's IP address on your computer's or mobile device's browser. Most of what you need can be accessed through the Dashboard, including the ability to configure PiPass.

# PiPass Customization
<b>Customizing Database Source</b>

The baseline database will use the Nintendo Zones worksheet found on FatMagic's database. This section will show you how to set up a custom source where you can easily define multiple custom configurations and load them on demand.

    +   Use your own or create a Google account to store your database.

Now, make a copy of this <a href="https://drive.google.com/open?id=1OfgyryUHeCPth76ziFT985XNLS-O5EXtjQDa0kA1L6M&authuser=0" target="_blank">spreadsheet</a> and save it on Google Drive. 

    +   You can copy the spreadsheet easily by clicking "File" -> "Make a copy...".
    
Publish your spreadsheet to the Web by clicking:

    +   "File" -> "Publish to the web..."
    +   "Publish"
    
Also, make sure to copy the URL link of that spreadsheet. Now, open up the PiPass Dashboard:

    +   Navigate to the PiPass Dashboard with your web browser.
    +   Click "PiPass".
    +   Click "Settings".

"PiPass DB Key" will be of interest. Take your spreadsheet's KEY and replace the previous KEY value. For example, the URL you just copied would look something like this:

    +   https://docs.google.com/spreadsheets/d/1OfgyryUHeCPth76ziFT985XNLS-O5EXtjQDa0kA1L6M/pubhtml

The KEY would be the value 1OfgyryUHeCPth76ziFT985XNLS-O5EXtjQDa0kA1L6M between /d/ and /pubhtml. So copy that KEY value and replace it with the previous KEY value.

Now you will need to enter the worksheet you want to use. "PiPass DB Worksheet" controls which worksheet to use. The default value of 1 selects the very first worksheet and the value of 2 selects the second worksheet. For example, setting PiPass DB Worksheet to the value of 2 would use the "nintendo_zones" worksheet in the templated spreadsheet that you just copied.

<b>PiPass Nintendo Zone Cycle Time</b>

By default, PiPass will be a particular Nintendo Zone for 15 minutes, before moving onto the next one. This should give you enough time to play all the mini-games before you get your next batch. If this time is too long or too short for you, you can edit this setting through the PiPass Dashboard.

<b>Advance PiPass</b>

If you want to manually advance PiPass to the next Nintendo Zone in the list, you can now. This gives greater control in how you Homepass.

    +  Click 'PiPass' in the dashboard.
    +  Click 'Advance'.

<b>Shuffle Nintendo Zones</b>

Like most of the settings, this feature can be enabled or disabled through the PiPass Dashboard. Enabling shuffling will visit Nintendo Zones in your current list in random order, ensuring that each pass-through is different.

<b>Updating PiPass</b>

PiPass can be updated through the dashboard. This will pull updates from the master branch and provide PiPass with 'bleeding edge' updates. Especially useful for those who are unfamiliar with Linux. Updating can be done by:

    +  Click 'PiPass' in the dashboard.
    +  Click 'Update'.

Please allow for 30 seconds for all the updates to complete.

# Hardware
I have listed some kits that are quite good if you will be purchasing a Raspberry Pi for the first time. I'm not asking for any donations, but if you will be purchasing any hardware, these Amazon referral links would be helpful. The pricing on these items are exactly the same as a non-referral.

Please let me know if any other hardware is compatible and I will add them to this list.

<b>Canadian Links</b>

<a href="http://www.amazon.ca/gp/product/B00T2U7R7I/ref=as_li_ss_tl?ie=UTF8&camp=15121&creative=390961&creativeASIN=B00T2U7R7I&linkCode=as2&tag=matthew084-20">Raspberry Pi 2 Model B 1GB</a><img src="http://ir-ca.amazon-adsystem.com/e/ir?t=matthew084-20&l=as2&o=15&a=B00T2U7R7I" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.ca/gp/product/B00GWTNYJW/ref=as_li_ss_tl?ie=UTF8&camp=15121&creative=390961&creativeASIN=B00GWTNYJW&linkCode=as2&tag=matthew084-20">CanaKit Raspberry Pi 2 (1GB) Ultimate Starter Kit (Over 40 Components: New Raspberry Pi 2 + WiFi Dongle + 8GB SD Card + Case + Power Supply and many more)</a><img src="http://ir-ca.amazon-adsystem.com/e/ir?t=matthew084-20&l=as2&o=15&a=B00GWTNYJW" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.ca/gp/product/B00OL8JSIM/ref=as_li_ss_tl?ie=UTF8&camp=15121&creative=390961&creativeASIN=B00OL8JSIM&linkCode=as2&tag=matthew084-20">Mini RT5370 150Mbps USB Wifi Wireless LAN Card 802.11 N/g/b Adapter with Antenna</a><img src="http://ir-ca.amazon-adsystem.com/e/ir?t=matthew084-20&l=as2&o=15&a=B00OL8JSIM" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<b>United States of America Links</b>

<a href="http://www.amazon.com/gp/product/B00T2U7R7I/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00T2U7R7I&linkCode=as2&tag=matthew08b-20&linkId=W2HA4PU55DSRWDWA">Raspberry Pi 2 Model B Project Board - 1GB RAM - 900 MHz Quad-Core CPU</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=matthew08b-20&l=as2&o=1&a=B00T2U7R7I" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.com/gp/product/B008XVAVAW/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B008XVAVAW&linkCode=as2&tag=matthew08b-20&linkId=IN557BBG3PJEAU7M">CanaKit Raspberry Pi 2 Complete Starter Kit with WiFi (Latest Version Raspberry Pi 2 + WiFi + Original Preloaded 8GB SD Card + Case + Power Supply + HDMI Cable)</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=matthew08b-20&l=as2&o=1&a=B008XVAVAW" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.com/gp/product/B00V39HVY0/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00V39HVY0&linkCode=as2&tag=matthew08b-20&linkId=D5PCSSC5K4XNMGXS">SunFounder RT5370 USB Wireless Network Wifi Adapter for Raspberry Pi with 2dBi Antenna - Plug and Play</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=matthew08b-20&l=as2&o=1&a=B00V39HVY0" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.com/gp/product/B0067NFSE2/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B0067NFSE2&linkCode=as2&tag=matthew08b-20&linkId=K7P7YF4R4Z3DFFQO">Protronix 150Mbps USB Wireless Network WIFI Adapter for Laptop Notebook 802.11N/G</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=matthew08b-20&l=as2&o=1&a=B0067NFSE2" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.com/gp/product/B00H95C0A2/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00H95C0A2&linkCode=as2&tag=matthew08b-20&linkId=W6TR3BCW32NGSPW7">Wifi With Antenna For Raspberry Pi - Instructions Included - PLUG and PLAY</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=matthew08b-20&l=as2&o=1&a=B00H95C0A2" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

# Future Features
I want to expand the functionality of PiPass by adding the following:

    +   Complete logging for debugging and historical analysis.

# Support
If you have any problems with PiPass, please let me know through my GitHub. I will do my best to help you out. Thanks for trying out PiPass!
