# ROG-STRIX-X570-E-GAMING
EFI for Ventura

# Specs:

- Motherboard: ROG STRIX X570-E GAMING
- CPU: AMD Ryzen 9 3900X
- GPU: Sapphire Nitro+ Radeon RX 590 8GB GDDR5
- Watercooler: Corsair H115i RGB Platinum
- RAM: 4x CORSAIR Vengeance LPX 16GB DDR4 3600Mhz
- NVMe: 2x SAMSUNG 980 M.2 2TB (Windows 10 and macOS Monterey)
- SSD: Crucial 500GB (Data for Windows)
- Wifi/Bluetooth: BCM94360CS2
- Monitor: AOC C24G1 144Hz

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
- Lilu.kext v1.6.2
- VirtualSMC.kext v1.3.0
- WhateverGreen.kext v1.6.2
- AppleALC.kext v1.7.7
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
