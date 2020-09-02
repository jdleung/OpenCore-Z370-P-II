# Opencore(0.6.0) configuration on Asus Prime Z370-P II

### Tested macOS

- Catalina

![Catalina](catalinaInfo.png)

- Mojave

![Mojave](mojaveInfo.png)

### Hardware

- Asus Z370-P II
- Intel i5 9400F
- Radeon RX 570 4GB
- Corsair 3000MHz 8GB * 2
- Intel SSD 250GB

#### Working

- Memory XMP
- Bluetooth, Wi-Fi and ethernet
- Airdrop
- Onboard Audio
- Sleep / Awake
- App Store
- Time Machine

***

### BIOS Settings

- OS type: other types

#### Disabled

- Fast Boot
- Launch CSM
- Vt-d 

#### Enabled

- Vt-x
- Above 4G decoding

***

### Misc

#### Update to new version OpenCore

- Download the newest OpenCore and OpenCore Configurator
- Create a new folder and copy folder `EFI` from the new OpenCore
- Copy `Sample.plist` from `Docs` to `EFI/OC`, and rename it to `config.plist`
- Set .efi files in `EFI/OC/Drivers` same as the old one
- Copy and update drivers in `kexts`: AppleALC.kext, IntelMausi.kext, Lilu.kext, SMCProcessor.kext, SMCSupperIO.kext, VirtualSMC, WhateverGreen.kext
- Keep RealtekRTL8111.kext in version 2.2.2 ( for my own hardware only )
- Copy SSDT file(if any) from old folder `ACPI` to new folder `ACPI`
- Open  `config.plist` , both new and old, in OpenCore Configurator, set the new one same as the old one
- For testing in safety, the new configuration should run on a bootable USB first

#### Conversion

* [Converting from Clover to OpenCore](/conversion.md)

