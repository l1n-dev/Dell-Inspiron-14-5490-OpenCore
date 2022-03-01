# Dell-Inspiron-14-5490-OpenCore

![image](https://user-images.githubusercontent.com/79068208/156099352-be17a6a1-64d3-428c-a4fd-ca65de19719e.png)


My OpenCore EFI folder for Hackintosh-ing.

NOTE: Go visit the [Wiki](https://github.com/TheNewEraBrad/Dell-Inspiron-14-5490-OpenCore/wiki) before doing anything in this repo.

My specs:  
Intel Core i5-10210U @ 1.60 GHz  
8GB DDR4-2667 SODIMM RAM (4GB soldered, 4GB additional)  
IM2P33F3 NVMe ADATA 256GB SSD  
Intel UHD Graphics 620 (0x9b41) (spoofed to 0x3e9b)  
NVIDIA GeForce MX 230 (Disabled via `-wegnoegpu`)  
Fenvi BCM94360NG Wireless card (802.11ac)  
Realtek USB Camera  
Shenzhen Goodix Fingerprint  

What works:  
Camera  
Built-in Speakers  
Battery Percentage Monitor  
HDMI & HDMI audio  
Trackpad gestures  
Backlight keys  
All USB Ports  
WiFi, Airdrop, Airplay and Bluetooth  

Untested:  
Displayport via USB-C (disabled in config.plist)  
Security lock  
Partially working:  
Sidecar (Connects 50% of the time, is an issue with macOS Monterey)  

Not working:  
Microphone (Intel SST)  
Headphone Jack (Also Intel SST)  
Disable NVIDIA GPU with SSDT (Freezes 10 seconds after login)  
Trackpad with SSDT-GPI0 (Trackpad OS Checking) SSDT-XOSI works fine though  
Fingerprint (Appears after USB Map but doesn't work)  

Known issues:  
Problem: Sometimes when booting, trackpad doesn't work.  
Solution: Reboot with Tab keys and Space bar.  

Problem: HDMI takes a while to initialize.  
Solution: There isn't really a solution, Comet Lake UHD 620 is not natively supported.  

Problem: Camera doesn't appear in System Info.  
Solution: Use SSDT-RHUB when installing (SSDT-USB-Reset is the same thing).  

Note: The serial number in `Platforminfo > Generic` is blanked out. You can generate a serial with [GenSMBIOS.](https://github.com/corpnewt/GenSMBIOS).  
Other note: USB Map Kext is removed because some variants of this laptop have different USB configurations.  
Other other note: My BIOS revision is 1.16.1, so please update to the latest Dell BIOS before proceeding.  
Last note I swear: My CFG Lock is disabled using [Dortania's method](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html) so if your CFG Lock is still enabled, enable `AppleXCPMCfgLock` in `Kernel > Quirks`. (ControlMSR32 reports CFG lock enabled, idk why).  
