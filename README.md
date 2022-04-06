# Dell-Inspiron-14-5490-OpenCore

![image](https://user-images.githubusercontent.com/79068208/156099352-be17a6a1-64d3-428c-a4fd-ca65de19719e.png)


My OpenCore EFI folder for Hackintosh-ing.

NOTE: Go visit the [Wiki](https://github.com/TheNewEraBrad/Dell-Inspiron-14-5490-OpenCore/wiki) before doing anything in this repo.

Update: Nowadays, I have quit the hackintosh scene and installed [Gentoo GNU/Linux](https://gentoo.org) with a new 20GB RAM upgrade. I probably won't be updating this anymore.

My specs:  
Intel Core i5-10210U @ 1.60 GHz.  
~8GB DDR4-2667 SODIMM RAM (4GB soldered, 4GB additional)~  
20GB DDR4-2667 SODIMM RAM (4GB soldered, 16GB additional).  
~IM2P33F3 NVMe ADATA 256GB SSD~  
Patriot P300 NVMe (512GB) (Doesn't seem to boot with macOS).  
Intel UHD Graphics 620 (0x9b41) (spoofed to 0x3e9b).  
NVIDIA GeForce MX 230 (Disabled via `-wegnoegpu`).  
Fenvi BCM94360NG Wireless card (802.11ac).  
Realtek USB Camera.  
Shenzhen Goodix Fingerprint.  

What works:  
Audio Out  
Power Management  
Camera  
Built-in Speakers  
Battery Percentage Monitor  
HDMI & HDMI audio  
Trackpad gestures  
Backlight keys  
All USB Ports  
WiFi, Airdrop, Airplay and Bluetooth  

Fixed:  
Sidecar (USB Map Issue)  
Headphone jack audio (Set `alcid=16` or `10000000` in `DeviceProperties`)

Untested:  
Displayport via USB-C (disabled in config.plist)  
Security lock  

Partially working:  
~Sidecar (Connects 50% of the time, is an issue with macOS Monterey)~  
See Fixed section.  

Not working:  
Microphone (Intel SST)  
Headphone jack input (Realtek issue)  
Disable NVIDIA GPU with SSDT (Freezes 10 seconds after login)  
Trackpad with SSDT-GPI0 (Trackpad OS Checking) SSDT-XOSI works fine though  
Fingerprint (Appears after USB Map but doesn't work, can be passed through to VMware Windows VM)  
Windows Dual-boot (SSDT-XOSI conflict)

Note: The serial number in `Platforminfo > Generic` is blanked out. You can generate a serial with [GenSMBIOS.](https://github.com/corpnewt/GenSMBIOS)  
Other note: USB Map Kext is removed because some variants of this laptop have different USB configurations.  
Other other note: My BIOS revision is ~1.16.1~ **1.17**, so please update to the latest Dell BIOS before proceeding.  
Last note I swear: My CFG Lock is disabled using [Dortania's method](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html) so if your CFG Lock is still enabled, enable `AppleXcpmCfgLock` in `Kernel > Quirks`. (ControlMSRE2 reports CFG lock enabled, idk why).  
