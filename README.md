# Hackintosh EFI for HP Envy 13-ad1xx  
**Updated for 2025 – Supports macOS Ventura, Sonoma, and Sequoia**

This EFI is a customized and optimized version of the OpenCore MOD EFI originally developed by [Olarila](https://olarila.com/), tailored specifically for the **HP Envy 13-ad1xx** series. It provides reliable compatibility with **macOS Ventura (13.x)**, **Sonoma (14.x)**, and **Sequoia (15.x)** as of March 2025.

The EFI is ready to use — **no tweaks required** unless you encounter specific issues.

## 🔧 Key Features
- **Pre-configured for Plug-and-Play Booting**  
  Includes `SSDT-XOSI.aml`, `VoodooPS2.kext`, and all necessary kexts and patches for trackpad, Intel Wi-Fi/Bluetooth, and power management.
- **Supports Intel Wireless Only**  
  Compatible with Intel Wi-Fi/Bluetooth cards like **AX200** and **AX201** using `itlwm.kext` and `IntelBluetoothFirmware.kext`.
- **Tested Across macOS Versions**  
  Verified working on **Ventura**, **Sonoma**, and **Sequoia** (including latest beta builds).

## 🚀 Quick Start

1. **Download the EFI**  
   Get the latest prebuilt EFI from the [Releases Section](https://github.com/Noobyetpro/Hp-Envy-13-ad1xx-hackintosh/releases) and copy it directly to your EFI partition.

2. **Inject SMBIOS Info**  
   Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate a unique SMBIOS (e.g., MacBookPro14,1 or iMac18,1). You can flash the SMBIOS Directly with GenSMBIOS.

3. **BIOS Settings**  
   Make sure your HP Envy’s BIOS is updated (F.18 or newer recommended). Disable **VT-d**, **CFG-Lock**, and **Secure Boot** if available.

4. **Boot macOS Installer**  
   Use a USB installer created with macOS Ventura/Sonoma/Sequoia. Boot with this EFI and proceed with installation.

## 🛠 Tweaks and Troubleshooting
All tweak-related info (e.g., boot-args, SIP, external display patches) has been moved to the [**TWEAKS.md**](./TWEAKS.md) file.  
Check it out **only if you run into issues** or need to customize for different hardware variations.

## ⚠️ Notes
- **No Tweaks Needed by Default** – Everything works out-of-the-box for most HP Envy 13-ad1xx models.
- **SIP** – Partially disabled (0x67) by default for compatibility.
- **Audio/USB-C Display** – May need extra patches. See [TWEAKS.md](./TWEAKS.md) for more details.

## 🙏 Credits
Based on the original EFI by **Olarila**. Big thanks to the Hackintosh community, especially:
- [Dortania Guides](https://dortania.github.io/OpenCore-Install-Guide/)
- [CorpNewt’s Tools](https://github.com/corpnewt)
- The many testers and contributors on Hackintosh forums & Discords


