## ⚠️ Converting from Clover

* [Guidance for converting from Clover to OpenCore](https://github.com/dortania/OpenCore-Desktop-Guide/tree/master/clover-conversion)


### Clear the cache

`- Terminal command: sudo kextcache -i /`


### Remove kexts in L/E (if any)

`- AHCI_3rdParty_eSATA.kext`

`- AHCI_3rdParty_SATA.kext`

`- AHCI_Intel_Generic_SATA.kext`

`- FakePCIID_XHCIMux.kext`

`- FakePCIID.kext`

`- FakeSMC.kext`

`- GenericUSBXHCI.kext`

`- NoVPAJpeg.kext`

`- NullCPUPowerManagement.kext`


### Replace kexts in L/E with OpenCore version's

`- Lilu.kext`

`- WhateverGreen.kext`

`- AppleALC.kext`

`- VirtualSMC.kext`


### Reset NVRAM

`- Boot Menu: Reset NVRAM`



