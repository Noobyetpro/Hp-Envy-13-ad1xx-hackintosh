# 🛠 TWEAKS.md  
**Advanced Configuration & Troubleshooting for HP Envy 13-ad1xx Hackintosh EFI**

This file contains optional tweaks, fixes, and advanced configurations for users who experience issues or want to customize their setup beyond the default EFI. If everything works out of the box — **you don’t need to change anything here.**

---

## ⚙️ Boot Arguments

You can modify boot arguments in `config.plist > NVRAM > Add > 7C436110-AB2A-4BBB-A880-FE41995C9F82 > boot-args`.

### Useful Boot Args:
| Argument                     | Purpose                                                    |
|-----------------------------|------------------------------------------------------------|
| `-v`                        | Verbose mode (see detailed boot logs)                      |
| `-lilubetaall`              | Enables Lilu on beta macOS versions like Sequoia           |
| `amfi_get_out_of_my_way=1`  | Required for some unsigned or patched kexts to load        |
| `keepsyms=1 debug=0x100`    | More detailed panic/debug logs (for debugging kernel issues)|
| `igfxfw=2`                  | Forces iGPU firmware loading (can help with graphics glitches)|

---

## 🔧 SIP (System Integrity Protection)

Default SIP setting: `csr-active-config=0x67` (partially disabled for kext injection and root patching)

If you want to:
- **Fully enable SIP**: set `csr-active-config=00000000`
- **Fully disable SIP**: set `csr-active-config=FF0F0000`

Modify this in:  
`config.plist > NVRAM > Add > 7C436110-AB2A-4BBB-A880-FE41995C9F82 > csr-active-config`

---

## 🖱 Trackpad Tweaks

If your trackpad isn't responsive or gestures aren’t working well:
- Try using the **debug version** of `VoodooPS2Controller.kext`
- Replace the existing kext with one from the [Acidanthera releases](https://github.com/acidanthera/VoodooPS2/releases)
- Enable `VoodooInput` in config.plist if not already enabled

---

## 🌐 Wi-Fi and Bluetooth (Intel Only)

### Supported Intel Cards
- **AX200**
- **AX201**
- **7265**, **8265**, and similar

### Required Kexts:
- [`itlwm.kext`](https://github.com/OpenIntelWireless/itlwm) or `AirportItlwm.kext` (choose based on desired UI)
- `IntelBluetoothFirmware.kext`
- `IntelBluetoothInjector.kext`

> Make sure you're using the correct version of the kexts for your macOS version (Ventura/Sonoma/Sequoia).  
> You can find compatible builds on the [OpenIntelWireless GitHub](https://github.com/OpenIntelWireless).

---

## 🧠 Power Management

### CPU Power Management
- ACPI patching handled by `SSDT-XOSI.aml` and `SSDT-PLUG.aml`
- For best results, ensure `CPUFriend.kext` is added and correctly paired with a `CPUFriendDataProvider.kext`

### Sleep Issues?
- Disable `Wake on LAN` in BIOS
- Confirm USB ports are mapped correctly
- Consider adding `SSDT-USBX.aml` if not already included

---

## 🖥 External Display (USB-C / HDMI)

USB-C to HDMI may not work out of the box. Try:
- Ensuring `WhateverGreen.kext` is loaded
- Enabling `igfxonln=1` boot arg
- Injecting framebuffer patches using `DeviceProperties > PciRoot(0x0)/Pci(0x2,0x0)`
  - Recommended ig-platform-id: `0x59160000` for Kaby Lake

---

## 🎧 Audio Fixes

The HP Envy 13-ad1xx typically uses **Realtek ALC283**.

If audio doesn’t work:
- Ensure `AppleALC.kext` is loaded
- Try layout IDs like `3`, `11`, or `13` 
