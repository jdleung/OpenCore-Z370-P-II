# Opencore(0.6.0) configuration on Asus Prime Z370-P II

![About My Mac](sysInfo.png)

### Tested macOS

- Mojave
- Catalina

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

- Download the newest OpenCore
- Download the newest OpenCore Configurator
- Create a new folder and copy folder `EFI` from the newest OpenCore to it
- Copy `Sample.plist` from `Docs` to `EFI/OC`, and rename it to `config.plist`
- Set .efi files in `EFI/OC/Drivers` same as to old the one
- Update drivers in `kexts`: AppleALC.kext, IntelMausi.kext, Lilu.kext, SMCProcessor.kext, SMCSupperIO.kext, VirtualSMC, WhateverGreen.kext
- Keep RealtekRTL8111.kext in version 2.2.2 ( for my own hardware only )
- Copy SSDT file(if any) from old folder `ACPI` to new folder `ACPI`
- Open  `config.plist` , both old and new, in OpenCore Configurator, set the new one same as the old one

#### Conversion

* [Converting from Clover to OpenCore](/conversion.md)

