### Big Sur hackintosh for Vaio Fit 15

**THIS IS ONLY FOR THE ORIGINAL FIT 15! THIS WILL NOT WORK FOR MODELS LIKE THE FIT 15A**. Make sure your BIOS is up to date, an outdated BIOS can cause problems with macOS. This EFI will only work with Big Sur.

Format your drive as FAT32, and follow [this guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/windows-install.html) for grabbing a copy of Big Sur. Even though it says it's for Windows only, it works for all OS's with Python. You can skip the formatting part -- format your drive as FAT32 via whatever your preferred method is.

![image](https://github.com/user-attachments/assets/64fd2645-7142-41d5-b19c-94af0d086cb4)

Specs of my specific Fit 15:
* CPU: Intel Core i5-3337U
* GPU 1: Intel HD Graphics 4000
* GPU 2: NVIDIA GeForce GT 735M
* RAM: 4GB soldered, 4GB slotted, DDR3
* Make/Model: Vaio Fit 15
* Audio Codec: Realtek ALC233
* Ethernet: Realtek RTL8111
* Wi-Fi card: Intel Centrino Wireless-N 6300
* Touchpad: Synaptics SMBus Clickpad
* Touchscreen: Atmel maXtouch USB

Current issues:
- Intel Bluetooth isn't working
- The NVIDIA GPU does not work due to being connected via Optimus. This will likely never work in macOS. This EFI disables it via wegnoegpu. Vaio does allow you to disable the NVIDIA GPU in the BIOS, however I leave it enabled and just disable it in macOS via the wegnoegpu bootarg, so I can use it in Windows or Linux. You can disable it in the BIOS if you want to. 

Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate a MacBookAir6,2 SMBIOS and copy the details to the appropriate sections in the `PlatformInfo` section of the config.plist. **macOS will not work if you don't do this!** Make sure the serial number is invalid. You can check at [Apple's Check Coverage](https://checkcoverage.apple.com) page. If it tells you to enter a valid serial number, you can safely use that serial number in your config.plist. If it gives you the purchase date for a MacBook Air, generate a new SMBIOS **AND DO NOT USE THE ONE WITH A VALID SERIAL NUMBER**. Using an SMBIOS with a valid SN can result in you losing your Apple ID. 

Set the following settings in your BIOS, macOS may not work properly if you don't:
- Advanced -> Intel(R) Virtualization Technology -> Enabled
- Security -> Secure Boot -> Disabled
- Boot -> Boot Mode -> UEFI

Once macOS is installed, follow [this guide](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html) to boot without a USB.
