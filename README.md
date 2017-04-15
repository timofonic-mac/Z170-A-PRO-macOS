# Z170-A-PRO-macOS
Guide and files for setting up macOS on the Z170-A PRO motherboard from MSI. This guide assumes you have a nvidia GPU and are using Ethernet.
---
0. Bios. 

The stock bios settings should work, just make sure you have CFG_LOCK disabled. Overclocking > CPU Features > CFG_LOCK. 

1. Creating the bootable USB drive.

This is very easy to do, just use unibeast to create a USB drive. Make sure when you call the USB Drive "macOS" when formatting it using disk utility,  though. Now copy "config_usb.plist" to "EFI/CLOVER/" and rename it to "config.plist". After that, copy all kexts from the kext directory to "EFI/CLOVER/kexts/Other/". Last, copy all the files from the SSDT folder to "EFI/CLOVER/ACPI/patched/". I lied about that being the last part, copy all the files from "drivers64UEFI" to "EFI/CLOVER/drivers64UEFI/". You should be done with the USB drive part.

2. Installing macOS. 

Reboot your computer and press "F11" while booting, it should show a USB boot screen. Select your USB drive. It should look like "UEFI: Sandisk Partition 1" if you have a Sandisk drive. After that, you'll see clover. Select the mountain with eyes and wait for it to load. You should get to a welcome to macOS screen, accept the license, click the utilities tab at the top bar, format the drive you want you use as Apple Extended HFS. Make sure the name of the drive is "macOS". Close Disk Utility and click next on the installer, select the disk, and click install. It should install. Once done installing, your PC should reboot.

3. Post-Install. 

After installing, select the USB drive again in your boot menu. This time it auto boot into the OS after 3 second, if not select the hard drive manually. Do the normal setup, create an account, accept the EULA, etc. Once done, you should be on the desktop. Open up safari and download [Clover Configurator.](http://mackie100projects.altervista.org/download-mac.php?version=vibrant) Once downloaded, open up the Clover Configurator app. If it doesn't let you, open up terminal by pressing Win + Space and typing Terminal and past this code in the terminal:
```
sudo spctl --master-disable
``` 
Once the app is open, it should ask you to mount a drive. Select your install hdd. I'll be labeled something like Disk1s1. If you don't know this, you can open disk utility and click on your disk to find out. Close clover, open it back up, and click the "Mount EFI" tab and mount your USB drive this time. If you don't know the disk number for the USB drive you can do the same steps again as with finding out the HDD disk number. Once the USB drive EFI partition is mounted and the USB drive EFI partition is mounted, copy the contents of the USB drive EFI partition to the disk partition, but replace the config.plist with the config_inst.plist file. Remove the USB drive. Now download the [nvidia web drivers](http://www.insanelymac.com/forum/topic/312525-nvidia-web-driver-updates-for-macos-sierra-update-03272017/) and install them. It'll ask you to reboot, press yes. While booting back up press "F11" again to enter the boot select menu. select your install HDD this time. It should boot back into macOS with no problems. Once logged in, open up system settings > sound > sound devices and select "internal speaker". You should now have sound. You're done! 
---
If you have any problems contact me on [twitter.](http://twitter.com/mikecoledotco) I made this guide off of the top of my head as I haven't reinstaleld macOS in a while, so I'm sure some things might be missing. Thanks to all the developers that made the kexts, drivers, DDST files and more.