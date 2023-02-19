# ROG-STRIX-X570-E-GAMING
EFI for Ventura

# Specs:

- Motherboard: ROG STRIX X570-E GAMING
- CPU: AMD Ryzen 9 3900X
- GPU: Sapphire Nitro+ Radeon RX 590 8GB GDDR5
- Watercooler: Corsair H115i RGB Platinum
- RAM: 4x CORSAIR Vengeance LPX 16GB DDR4 3600Mhz
- NVMe: 2x SAMSUNG 980 M.2 2TB (Windows 11 and macOS Monterey)
- Wifi/Bluetooth: BCM94360CS2
- Monitor: 2x AOC C24G1 144Hz
- Bootloader: OC 0.8.9
- SMBios: MacPro 7,1
- macOS: Ventura 13.2.1


# BIOS Settings

- Enter BIOS -> Press Delete -> Enter Setupv1.0
- Exit -> Load Optimised Defaults
- Ai Tweaker -> Ai Overclock Tuner -> D.O.C.P.
- Advanced -> APM Configuration -> Power On By PCIe -> Disabled
- Advanced -> PCI Subsystem Settings -> Above 4G Decoding -> Enabled
- Advanced -> PCI Subsystem Settings -> Re-Size BAR Support -> Disabled
- Advanced -> USB Configuration -> Legacy USB Support -> Auto or Disabled
- Boot -> Boot Configuration -> Fast boot -> Disabled
- Boot -> CSM -> Launch CSM -> Disabled
- Boot -> Secure boot -> OS Type -> Windows UEFI mode
- Boot -> Secure boot -> Key Management -> Clear Secure Boot Keys


# ACPI SSDT's - All bypassed for other OS
- SSDT-HPET.aml (HPET _CRS (Needs _CRS to XCRS Rename))
- SSDT-PLUG.aml (CPU power management)
- SSDT-SBRG.aml (Correcting EC, RTC memory & IRQ conflicts)
- SSDT-SBUS-MCHC.aml (SMBus Support)
- SSDT-USBX.aml (USB power tables)
- SSDT-GPU-6950XT.aml (GPU Spoof through bridge)


# Kexts

- Lilu.kext v1.6.3
- VirtualSMC.kext v1.3.0
- WhateverGreen.kext v1.6.3
- AppleALC.kext v1.7.8
- AirportBrcmFixup.kext v2.1.6
- SmallTreeIntel82576.kext v1.0
- LucyRTL8125Ethernet.kext v1.1.0
- AppleMCEReporterDisabler.kext
- BlueToolFixup.kext v2.6.4
- BrcmFirmwareData.kext v2.6.4
- BrcmPatchRAM3.kext v2.6.4
- AMDRyzenCPUPowerManagement.kext v0.7.1
- SMCAMDProcessor.kext
- RestrictEvents.kext v1.0.9
- NVMeFix.kext v1.1.0
- RadeonSensor.kext v0.3.1
- SMCRadeonGPU.kext v0.3.1
- USBMap.kext - ASUS ROG STRIX X570-E with/without wifi-bluetoth pcie card
- IntelBTPatcher.kext v2.2.0 (Disabled by default)
- IntelBluetoothFirmware.kext v2.2.0 (Disabled by default)

# INSTALL NOTES​
Using PlistEdit Pro, Xcode or ProperTree add your details by modifying the following
<img width="646" alt="1126595787_Screenshot2020-01-16at19_25_01 png 890a13d93c1ce4f42ee7dedb6d156e1e" src="https://user-images.githubusercontent.com/58921288/210339017-080d141a-0732-458b-ba3e-4f751a405665.png">

# WIFI / BLUETOOTH​

## IF NOT USING A BROADCOM WIFI PCI-E CARD

If you are using internal Intel wifi-bluetooth, use Intel wifi-bluetooth kext. Just enable the two intel-related entries under Kernel -> Add and disable the two entries which start with Brcm. Also rename USBMap.kext to USBMap(Broadcom).kext and rename USBMap(with Intel BT).kextUSBMap(with Intel BT).kext to USBMap.kext

# GPU​

## IF NOT USING AMD RX 6950 XT

Remove EFI/OC/ACPI/SSDT-GPU-6950XT.aml and remove it from conflig.plist ( ACPI -> Add ).

## IF NOT USING AMD RDN2 GRAPHIC CARD 

Remove agdpmod=pikera from bootflags.

# CPU​

## IMPORTANT - PATCH INFO FOR SETTING THE CORRECT CORE COUNT FOR YOUR CPU
Core Count patch needs to be modified to boot your system. Find the two algrey - Force cpuid_cores_per_package patches and alter the Replace value only.

Changing BA000000 0000/BA000000 0090* to BA <CoreCount> 0000 0000/BA <CoreCount> 0000 0090* substituting <CoreCount> with the hexadeciamal value matching your physical core count.

Note: The three different values reflect the patch for different versions of macOS. Be sure to change all three if you boot macOS 10.13 to macOS 12

See the table below for the values matching your CPU Core Count.

| CoreCount	| Hexadecimal |
| --------- | ----------- |
|  6 Core   |      06     |
|  8 Core   |      08     |
| 12 Core   |      0C     |
| 16 Core   |      10     |
| 32 Core   |      20     |
  
  
So for example a 6 Core 5600X would result in these replace values, BA 06 0000 0000/BA 06 0000 0090
Or a 12 Core 5900X that I have it setup as standard would result in these replace values, BA 0C 0000 0000/BA 0C 0000 0090

