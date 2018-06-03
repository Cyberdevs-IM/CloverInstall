This Branch is for SuperMicro X8DAL-3 system with the following specs:

2 Intel XEON X5670 @ 2.93 GHz

24GB Ram DDR3 1600

Seagate 1 TB

HIS AMD Radeon HD 6790 1GB GDDR
(Device ID for this card needs to be added to AMD6000Controller.kext and AMDRadeonX3000.kext for Sierra and AMDLegacySupport.kext as well for High Sierra.)

PCIe USB 3.0 Expansion card

What works:

Everything, except for the Dual GigaBit Ethernet controllers which need the device ID to be added to the AppleIntelIE1000e.kext inside the IONetworkFamily.kext or just add the patched AppleIntelIE1000e.kext inside the \EFI\Clover\kext\Other folder.
