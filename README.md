# Dell-Inspiron-14-5490-OpenCore

![image](https://user-images.githubusercontent.com/79068208/156099352-be17a6a1-64d3-428c-a4fd-ca65de19719e.png)


### My OpenCore EFI folder for Hackintosh-ing.

## NOTE: This EFI folder is _very_ outdated, use something like OpCore-Simplify instead if you want a more updated and functional hackintosh. This repo exists only for historical purposes.

My specs:  
Intel Core i5-10210U @ 1.60 GHz  
20GB DDR4-2667 SODIMM RAM (4GB soldered, 16GB additional)  
Intel UHD Graphics 620 (0x9b41) (spoofed to 0x3e9b)  
NVIDIA GeForce MX 230 (Disabled via `-wegnoegpu`)  
Fenvi BCM94360NG Wireless card (802.11ac)  

## What works:  
All USB Ports[^1]  
Audio Out  
Backlight keys  
Battery Percentage Monitor  
Built-in Speakers  
Camera  
HDMI & HDMI audio  
Power Management  
Sidecar  
Trackpad gestures  
WiFi, Airdrop, Airplay and Bluetooth  

## What doesn't work:  
Internal & Headphone jack microphone[^2]  
Windows Dual-Boot

## Untested:  
Displayport via USB-C (disabled in config.plist)  
Security lock  

## Partially working:  
Headphone jack audio[^3]  
Fingerprint sensor[^4]  

## Additional Notes:

The serial number in `Platforminfo > Generic` is blanked out. You can generate a serial with [GenSMBIOS.](https://github.com/corpnewt/GenSMBIOS)  
My CFG Lock is disabled using [Dortania's method](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html) so if your CFG Lock is still enabled, enable `AppleXcpmCfgLock` in `Kernel > Quirks`. (ControlMSRE2 reports CFG lock enabled, idk why).  

[^1]:Create your own USBMap kext to load, this EFI doesn't contain any.
[^2]:The microphone and headphone jack input will likely **never** work on macOS due to Intel's SST, which never had a driver released or kext developed for it.
[^3]:You must set `alcid=16` or `10000000` in `DeviceProperties`. Changing the `alcid` causes instability with main speakers.
[^4]:Using the sensor natively doesn't work, but it does function if passed through to a Windows virtual machine.
