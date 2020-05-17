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

- OS type: other types

#### Disabled

- Fast Boot
- CSM
- Advanced \ Chipset Configuration → Vt-d 
- Advanced \ Super IO Configuration → Serial Port

#### Enabled

- Vt-x
- Above 4G decoding
- Execute Disable Bit
- Advanced \ USB Configuration → XHCI Hand-off 



## ⚠️ Caution

If OpenCore is converted from a using Clover, the following may help you remove panic on booting.

* [Guidance for converting from Clover to OpenCore](https://github.com/dortania/OpenCore-Desktop-Guide/tree/master/clover-conversion)


#### Clear the cache

`- Terminal command: sudo kextcache -i /`

`- Boot Menu: Reset Nvram`


#### Remove kexts in L/E (if any)

`- AHCI_3rdParty_eSATA.kext`

`- AHCI_3rdParty_SATA.kext`

`- AHCI_Intel_Generic_SATA.kext`

`- FakePCIID_XHCIMux.kext`

`- FakePCIID.kext`

`- FakeSMC.kext`

`- GenericUSBXHCI.kext`

`- NoVPAJpeg.kext`

`- NullCPUPowerManagement.kext`


#### Replace kexts in L/E with OpenCore version's

`- Lilu.kext`

`- WhateverGreen.kext`

`- AppleALC.kext`

`- VirtualSMC.kext`






