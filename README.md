# ASUS-Vivobook-X415JA-R465JA-OpenCore

[![OpenCore Version](https://img.shields.io/badge/OpenCore-0.9.3-green.svg)](https://github.com/SkyrilHD/Dell-E7250-Hackintosh/)
[![GitHub release](https://img.shields.io/github/tag/TECHNIKVERBOT/ASUS-Vivobook-X415JA-R465JA-OpenCore.svg)](https://github.com/TECHNIKVERBOT/ASUS-Vivobook-X415JA-R465JA-OpenCore/releases/)
[![GitHub issues](https://img.shields.io/github/issues/TECHNIKVERBOT/ASUS-Vivobook-X415JA-R465JA-OpenCore.svg)](https://github.com/TECHNIKVERBOT/ASUS-Vivobook-X415JA-R465JA-OpenCore/issues/)
 
### Before you give this EFI a try, make sure you read [this](#generating-your-own-serial-and-editing-rom)!

This repo includes an OpenCore EFI for the ASUS Vivobook X415JA.

Testing on:

Model | ASUS Vivobook X415JA
------------- | ---------------
CPU | Intel Core i3-1005G1
iGPU | Intel UHD Graphics G1
RAM | 8 GB DDR4
WiFi | Realtek 8821CE (not supported)
macOS | Ventura 13.0

## What works?

- Audio
- Battery readout
- Boot
- Brightness Control
- GPU acceleration
- Keyboard + Trackpad
- Power Management
- SD card reader
- Sleep
- USB
- Webcam
- Speaker

## What doesn't work?

- HDMI Output
- headphone jack (untested)
- SD card reader (untested)
- Apple ID login
    - requires a supported internal network adapter
    (Ethernet (doesn't exist) or a compatible WiFi card)
- WiFi / Bluetooth
    - Realtek WiFi cards are not supported, replace it with an Intel (basic functionality) or a Broadcom one (full feature set, Ventura and older)
    - added HoRDNIS so a tethered wifi connection from an Android phone can be used instead
- Intel Optane H10 (stock SSD)
    - Either change your SSD or use an external drive
        - If you are using an external drive, add `nvme=-1` to your boot-args to avoid kernel panics

## BIOS settings

- Secure Boot: Disabled
- TBD

## How to install

Download this repo and place the EFI folder into your internal drive's EFI partition... That's it.

## How to Install macOS Ventura

There are two ways you can install Ventura:

1. If you have an already working macOS, download the Installer from the App Store and make a bootable Installer with `createinstallmedia` by using this command in Terminal: `sudo /Applications/Install\ macOS\ Ventura.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery) from the offical [OpenCore release package](https://github.com/acidanthera/OpenCorePkg/releases/). Follow this [guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) to understand how it works.

After you have created a bootable Installer, copy the EFI folder to the EFI partition and install as usual. After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookAir9,1

Use Xcode, ProperTree or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

You should also put in your ethernet adapter's MAC address into the ROM section.

## Credits

* [1Revenger1](https://github.com/1Revenger1) (for ECEnabler)
* [acidanthera](https://github.com/acidanthera) (for OpenCore and the kexts)
* [dortania](https://dortania.github.io/OpenCore-Install-Guide/) (for their awesome guide)
* [jwise](https://github.com/jwise) (for HoRNDIS)
* [VoodooI2C](https://github.com/VoodooI2C) (for VoodooI2C)
* our tester
