macOS Catalina EFI for the Vaio Fit 15 using OpenCore. I will try to keep this EFI up to date with the latest OpenCore and kexts

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/affcaae3-1e4b-4918-9238-cb3177bf7aa8" />

# WARNING! SMBIOS DETAILS ARE NOT INCLUDED IN THE CONFIG.PLIST.
You will have to use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate a **MacBookAir5,2** SMBIOS for your system, and add them to the config.plist.

## Other macOS versions?
No. Catalina is the latest supported by MacBookAir5,2, so it's all I'll ever support. If you want a different version, feel free to fork this repo to modify it for whatever version you want. Do note newer versions will likely require OCLP.

## System specs
Do note if your hardware differs, while unlikely, you may have issues. **THIS ONLY WORKS FOR THE SONY MODEL. DO NOT USE FOR THE NON-SONY FIT 15.**
- CPU: Intel Core i5-3337U
- GPU 1: Intel HD Graphics 4000
- GPU 2: NVIDIA GeForce GT 735M
- Chipset: Intel HM76
- Touchpad: Synaptics SMBUS
- Audio: Realtek ALC233
- Wi-Fi: Broadcom BCM43142
- Ethernet: Realtek RTL8111
- Disk: Samsung Momentus 1TB 5400RPM 2.5"

## Issues:
- Wi-Fi does not work. The BCM4314 chipset used in the Fit 15's card is not supported. I'd recommend replacing it with a supported Broadcom card.
- The GT 735M does not and will never work in macOS due to it using Optimus. The 735M is disabled in the config.plist.
- The HDMI port does not work, as the Fit 15 routes it through the 735M, even when it's disabled in the BIOS.
- Brightness keys do not work. BrightnessKeys does not support the Fit 15's configuration.

If you notice any other problems, please open an issue (or pull request if you have a fix)

### BIOS settings
If you do not set these BIOS settings, macOS will **not** boot.
- Advanced -> Intel(R) Virtualization Technology -> Enabled
- Security -> Secure Boot -> Disabled
- Boot -> Boot Mode -> UEFI
