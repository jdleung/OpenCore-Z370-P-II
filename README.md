# Opencore(0.5.8) configuration on Asus Z370-P II

![About My Mac](sysInfo.png)

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


### BIOS Settings

- Fast Boot: Disabled
- CSM: Disabled
- Vt-x: Enabled
- Above 4G decoding: Enabled
- Execute Disable Bit: Enabled
- OS type: other types
- Advanced \ Chipset Configuration → Vt-d : Disabled
- Advanced \ Super IO Configuration → Serial Port: Disabled
- Advanced \ USB Configuration → XHCI Hand-off : Enabled

### ⚠️ Caution

This OC boot loader is migrated from Clover, panics may occur on booting. The following operations can solve my problem

#### Kexts (if any) to be removed from L/E
- AHCI_3rdParty_eSATA.kext
- AHCI_3rdParty_SATA.kext
- AHCI_Intel_Generic_SATA.kext
- FakePCIID_XHCIMux.kext
- FakePCIID.kext
- FakeSMC.kext
- GenericUSBXHCI.kext
- NoVPAJpeg.kext
- NullCPUPowerManagement.kext

#### Clear the cache

- Terminal command: sudo kextcache -i /
- Boot Menu: Reset Nvram

#### Kexts to be replaced with the OpenCore version
- Lilu.kext
- WhateverGreen.kext
- AppleALC.kext
- VirtualSMC.kext






