# OpenCore(0.9.5) configuration on Asus Prime Z370-P II

![System Info](sysInfo.png)

## Tested macOS

- 0.9.5 
  - Ventura 13.5.2
  - Monterey 12.5.1
- 0.7.6 
  - Monterey 12.1, 12.5.1
  - Big Sur 11.6.1
- 0.7.0
  - Big Sur 11.0.1
  - Mojave
- 0.5.8 - 0.6.4
  - Catalina
  - Mojave

## Hardware

- Asus Z370-P II

- Intel i5 9400F

- Radeon RX 570 4GB

- Corsair 2133MHz 8GB * 2

- HIKVISION SSD C2000Pro 512G

- Intel SSD 250GB

- BCM943602CS / BCM94360CD BT4.1

#### Working

- Bluetooth, Wi-Fi and ethernet
- AirDrop, AirPlay
- Continuity
- Handoff
- Onboard Audio
- Sleep / Awake
- App Store
- Time Machine

***

## BIOS Settings

- OS type: other types

#### Disabled

- Fast Boot
- Launch CSM
- Vt-d 
- CFG Lock

#### Enabled

- Memory XMP (Adding 3 SSDT files should have fixed video glitches)
- Vt-x
- Above 4G decoding

***

## Misc

### CPU with Processor Graphics

The current configuration is for a -F series CPU. If you have an Intel CPU with Processor graphic, add this in config.plist

DeivceProperties

- Deivce: PciRoot(0x0)/Pci(0x2,0x0)
- Key: AAPL,ig-platform-id
- Value: 0300913E
- Type: Data

Most device addresses should be `PciRoot(0x0)/Pci(0x2,0x0)`, if not, use [gfxutil](https://github.com/acidanthera/gfxutil) to find it out.

```sh
gfxutil -f IGPU
```

| Value    | Comment                                                                                 |
|:-------- |:--------------------------------------------------------------------------------------- |
| 07009B3E | Used when the Desktop iGPU is used to drive a display                                   |
| 00009B3E | Alternative to `07009B3E` if it doesn't work                                            |
| 0300913E | Used when the Desktop iGPU is only used for computing tasks and doesn't drive a display |

[Details](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#deviceproperties)

### Disabled USB Ports

On 0.7.6+, two USB 2.0 ports at the rear of the motherboard are disabled so as to make the bluetooth works (you can customize your own USBPorts.kext). 4 external USB ports and 4 internal USB ports are still in use.

![Disabled USB Ports](disabled-usb-ports.png)

### Cannot update to newer versions of Big Sur

```sh
# Unenroll from beta catalog
sudo /System/Library/PrivateFrameworks/Seeding.framework/Resources/seedutil unenroll
# Enroll back in
sudo /System/Library/PrivateFrameworks/Seeding.framework/Resources/seedutil enroll DeveloperSeed
```

[Details](https://dortania.github.io/OpenCore-Install-Guide/extras/big-sur/#cannot-update-to-newer-versions-of-big-sur)

### Update OpenCore to the latest version

1. Download the latest [OpenCore](https://github.com/acidanthera/OpenCorePkg) 
   
    /X64/EFI/OC
   
   - ACPI
     
     - Copy SSDT files from the prvious version
   
   - Drivers
     
     - Keep same files as the previous version
   
   - Kexts (update the following files to the latest version)
     
     - **Copy USBPorts.kext from the previous version**
     
     - [IntelMausi.kext](https://github.com/acidanthera/IntelMausi)
     
     - [Lilu.kext](https://github.com/acidanthera/Lilu)
     
     - [VirtualSMC.kext, SMCProcessor.kext, SMCSupperIO.kext](https://github.com/acidanthera/VirtualSMC)
     
     - [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen)
     
     - [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X)
     
     - [AppleALC.kext](https://github.com/acidanthera/AppleALC)
     
     - [NVMeFix.kext](https://github.com/acidanthera/NVMeFix)

2. Download the latest [OpenCore Configurator](https://mackie100projects.altervista.org/)
   
    Open  `Docs/Sample.plist` and `config.plist`  in OpenCore Configurator, set the same configurations in `Sample.plist` as `config.plist`

3. Replace the old EFI folder with the new one
   
    For safety, the new configuration should be tested on a bootable USB first

### Hide debug information when release

config.plist

- Misc
  
  - Boot
    - Check `HideAuxillary`
  - Debug
    - target=0
    - AppleDebug=No
    - ApplePanic=No

- NVRAM
  
  - Add
    - 7C436110-AB2A-4BBB-A880-FE41995C9F82
      - boot-args: remove `-v`

- PlatformInfo
  
  - Generate your own System Serial Number

### Check OpenCore Version

The current version should be displayed on the boot menu screen, also you can get it in the terminal (you may need to reset NVRAM in boot menu first)

```sh
nvram 4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102:opencore-version
```

### Set Default Boot Entry

- Select a boot entry, then `Ctrl` + `Enter`

### Show Auxillary on Boot Entry

- Press `space bar` on boot entry screen

### Conversion

* [Converting from Clover to OpenCore](/conversion.md)
