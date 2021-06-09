# OpenCore(0.7.0) configuration on Asus Prime Z370-P II

![System Info](sysInfo.png)

### Tested macOS

- Big Sur
- Catalina (tested below v0.7.0)
- Mojave (tested below v0.7.0)

### Hardware

- Asus Z370-P II
- Intel i5 9400F
- Radeon RX 570 4GB
- Corsair 2133MHz 8GB * 2
- HIKVISION SSD C2000Pro 512G
- Intel SSD 250GB

#### Working

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
- ~~Memory XMP (cursor may randomly show as video glitches)~~

#### Enabled

- Memory XMP (Adding 3 SSDT files should have fixed video glitches)
- Vt-x
- Above 4G decoding

***

### Misc

#### Update to new version OpenCore

- Download the latest [OpenCore](https://github.com/acidanthera/OpenCorePkg) and [OpenCore Configurator](https://mackie100projects.altervista.org/)
- Create a new folder and copy folder `EFI` from the new OpenCore
- Copy `Sample.plist` from `Docs` to `EFI/OC`, and rename it to `config.plist`
- Set .efi files in `EFI/OC/Drivers` same as the old one
- Copy and update drivers in `kexts`: [IntelMausi.kext](https://github.com/acidanthera/IntelMausi), [Lilu.kext](https://github.com/acidanthera/Lilu), [VirtualSMC, SMCProcessor.kext, SMCSupperIO.kext](https://github.com/acidanthera/VirtualSMC), [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen)
- ~~Keep RealtekRTL8111.kext in version 2.2.2 ( for my own hardware only )~~
- Copy SSDT file(if any) from old folder `ACPI` to new folder `ACPI`
- Open  `config.plist` , both new and old, in OpenCore Configurator, set the new one same as the old one
- For testing in safety, the new configuration should run on a bootable USB first

#### Release

Config.plist

Misc -> Debug

- target=0
- AppleDebug=No

NVRAM -> Add -> 7C436110-AB2A-4BBB-A880-FE41995C9F82

- boot-args: remove `-v`

#### Check OpenCore Version

The current version should be display on the top of the boot menu, also you can get it in the terminal (you may need to reset NVRAM in boot menu first)

`nvram 4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102:opencore-version`

#### Default Boot Entry

- Select a boot entry, then `Ctrl` + `Enter`

#### Conversion

* [Converting from Clover to OpenCore](/conversion.md)

