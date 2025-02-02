# EFI for Asus TUF B450-Pro Gaming

## Overview

This is a pre-configured EFI folder for OpenCore 1.0.3, designed to work with macOS Sonoma and potentially all macOS versions down to Mojave.

<p align="center">
  <img src="https://github.com/user-attachments/assets/5ad9b84d-ef5b-4744-8083-d9b3ce73cea6" width="35%">
</p>

## Hardware Compatibility

| Component       | Model                                      |
|---------------|-------------------------------------------|
| **Motherboard** | Asus TUF B450-Pro Gaming                |
| **Processor**  | AMD Ryzen 5 3600                         |
| **CPU Cooler** | Deepcool GAMMAXX GTE V2 RGB              |
| **GPU**        | XFX RX 5700 XT Triple Dissipation 8GB    |
| **RAM**        | Kingston Fury DDR4 16GB 3200 RGB (x1)    |
| **Bluetooth**  | CSR 8510 A10                             |
| **Case**       | Gamdias Aura GC6 ARGB                    |

<img src="https://github.com/user-attachments/assets/20789c98-faa2-4f82-8299-7d2ee771288a" width="55%">

## What Works

✅ Bluetooth  
✅ DRM Content  
✅ Adobe Software  
✅ Audio  
✅ Stable System Performance  
✅ Thunderbolt Support  
✅ iPhone Sync (Not to be confused with Screen Mirroring)  
✅ FileVault  

<img src="https://github.com/user-attachments/assets/e53eed06-504a-4aef-995e-c06d3ee4800c" width="55%">

## What Doesn't Work

❌ Wi-Fi (No module installed)  
❌ AirDrop (Requires a Broadcom module)  
❌ ASUS Aura Sync (Unknown fix)  

## Tested OS

- ✅ macOS Sonoma  

## Working OS

🟡 macOS Catalina *(needs testing)*  
🟡 macOS Big Sur *(needs testing)*  
🟡 macOS Monterey *(needs testing)*  
🟡 macOS Ventura *(needs testing)*  
🟢 macOS Sonoma *(fully working)*  
🟢 macOS Sequoia *(fully working)*  

## Installation Guide

### 1. Preparing the USB Drive (Windows)
1. **Change SMBIOS** using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) before installation to ensure compatibility and proper iServices functionality.
2. Download **Python 3** and install it.
3. Download **OpenCorePkg** and extract it.
4. Open the **macrecovery** folder inside OpenCorePkg.
5. In the folder path, type `cmd` and press Enter to open Command Prompt.
6. Run the following command to download macOS recovery files:
   ```sh
   py macrecovery.py -b Mac-226CB3C6A851A671 -m 00000000000000000 download
   ```
7. Format a **USB drive (4GB+):**
   - Open **Disk Management**.
   - Delete all partitions on the USB.
   - Create a **FAT32** partition and name it **EFI**.
8. Create a folder on the USB:
   ```sh
   com.apple.recovery.boot
   ```
9. Move the **BaseSystem.dmg** and **BaseSystem.chunklist** files to this folder.

### 2. Creating the USB Installer
- **Option 1: Disk Management (UEFI systems)**
  - Format USB as **FAT32**.
  - Move macOS recovery files to `com.apple.recovery.boot`.
  - Copy the OpenCore **EFI** folder to the USB root.

- **Option 2: Rufus (USB 16GB+)**
  - Open **Rufus**.
  - Set **BOOT Selection** to **Non-Bootable**.
  - Set **File System** to **Large FAT32**.
  - Click **Start**, then remove any **autorun** files on the USB.
  - Move macOS recovery files to `com.apple.recovery.boot`.
  - Copy the OpenCore **EFI** folder to the USB root.

### 3. Configuring BIOS
1. Enter BIOS by pressing `F2` or `DEL` on boot.
2. Apply the following settings:
   - Disable **Secure Boot**
   - Enable **Above 4G Decoding**
   - Set **CSM** to **Disabled**
   - Set **SATA Mode** to **AHCI**
   - Enable **XMP Profile** (if applicable)
   - Set **Primary Display** to **PEG** (for external GPU users)
3. Save and exit BIOS.

### 4. Installing macOS
1. Boot from the USB drive and select **Install macOS**.
2. Follow the macOS installation steps.
3. After installation, boot into macOS using the USB (selecting **macOS** in OpenCore).

### 5. Post-Installation
1. Mount the internal drive's EFI partition.
2. Copy the EFI folder from the USB drive to the internal EFI partition.
3. Reboot and verify that OpenCore boots macOS properly.

![Screenshot 2025-02-02 at 23 14 38](https://github.com/user-attachments/assets/59d842f9-5224-4f39-b600-6a2bcd6679d4)
![Screenshot 2025-02-02 at 23 40 34](https://github.com/user-attachments/assets/0be560b2-b434-49bd-8849-09b614f63e08)
*Screenshot of working DRM content*

## Notes

- **For AirDrop and full macOS Wi-Fi support**, a Broadcom Wi-Fi module is required.
- **Aura Sync is not functional**; potential fixes need further research.

