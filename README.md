The README is already built — here it is ready to copy-paste:

---

```markdown
<div align="center">

# 🔥 HyperOS 3 — Infinix Zero 30 5G

### Unofficial port of Xiaomi HyperOS 3 to the Infinix Zero 30 5G

**Donor:** Xiaomi 15T Pro `lipa` (Dimensity 9400+)  
**Target:** Infinix Zero 30 5G `X6731-GL` (Dimensity 1200 / MT6893)  
**Maintainer:** [Alan](https://github.com/YOUR_USERNAME)  
**Status:** 🚧 Work In Progress — Alpha



![Device](https://img.shields.io/badge/Device-Infinix%20Zero%2030%205G-orange?style=flat-square)




![ROM](https://img.shields.io/badge/ROM-HyperOS%203-red?style=flat-square)




![Status](https://img.shields.io/badge/Status-Alpha-yellow?style=flat-square)




![Chipset](https://img.shields.io/badge/Chipset-Dimensity%201200-blue?style=flat-square)



</div>

---

## 📱 Device Information

| Property | Details |
|---|---|
| **Device** | Infinix Zero 30 5G |
| **Codename** | X6731 / X6731-GL |
| **Chipset** | MediaTek Dimensity 1200 (MT6893) |
| **Architecture** | arm64-v8a |
| **Android Base** | Android 14 |
| **Donor ROM** | Xiaomi HyperOS 3 (Xiaomi 15T Pro — `lipa`) |
| **Donor Chipset** | MediaTek Dimensity 9400+ |
| **Build Tool** | MIO-KITCHEN 4.1.8 |
| **Maintainer** | Alan |

---

## ✅ Working Status

| Feature | Status | Notes |
|---|---|---|
| Boot | ✅ Working | Reaches system UI |
| Display | ✅ Working | |
| Touchscreen | ✅ Working | |
| Wi-Fi | ✅ Working | |
| Bluetooth | ✅ Working | |
| Mobile Data | ✅ Working | |
| SIM / Calls | ✅ Working | |
| Audio | ✅ Working | |
| Vibration | ✅ Working | |
| USB | ✅ Working | |
| Settings App | ✅ Working | |
| Flashlight | ⚠️ Partial | QS tile missing (overlay issue) |
| Widgets | ⚠️ Partial | Some missing (overlay issue) |
| Camera | ❌ Not Working | Requires Infinix vendor HAL blobs |
| Fingerprint | ❌ Not Working | Goodix HAL mismatch |
| Face Unlock | ❌ Not Working | Biometrics stack issue |
| IHyperOSCustFeature | ❌ Broken | Null service — stub needed |
| MTK Deep Idle (SODI) | ❌ Disabled | Xiaomi power HAL incompatibility |

> **Legend:** ✅ Working &nbsp;|&nbsp; ⚠️ Partial &nbsp;|&nbsp; ❌ Not Working &nbsp;|&nbsp; 🔍 Untested

---

## 📥 Downloads

> ⚠️ **This is an alpha build. Do not use as daily driver. Always have a backup.**

Check the [**Releases**](../../releases) tab for the latest flashable zip.

---

## 📋 Prerequisites

Before flashing, make sure you have:

- [ ] Unlocked bootloader on your Infinix Zero 30 5G
- [ ] ADB & Fastboot installed on your PC
- [ ] Latest Infinix stock ROM backed up
- [ ] At least 80% battery charge
- [ ] USB cable (preferably USB-C to USB-A/C data cable)
- [ ] `payload-dumper-go` (for extracting if needed)

---

## 🔧 Installation Guide

> **Warning:** This will wipe your device. Back up everything first.

### Step 1 — Enter Fastboot Mode
```bash
adb reboot bootloader
# or hold Volume Down + Power while powering on
```

### Step 2 — Verify device is detected
```bash
fastboot devices
```

### Step 3 — Flash the ROM
```bash
# Flash super partition
fastboot flash super super.img

# Flash boot
fastboot flash boot boot.img

# Flash vendor_boot (if applicable)
fastboot flash vendor_boot vendor_boot.img

# Wipe userdata
fastboot -w
```

### Step 4 — Reboot
```bash
fastboot reboot
```

> First boot may take **5–10 minutes**. Do not panic.

---

## 🛠️ Build Guide (For Developers)

### Requirements
- Linux (Fedora / Ubuntu recommended)
- MIO-KITCHEN 4.1.8
- `payload-dumper-go`
- At least 60GB free disk space

### Step 1 — Extract Donor ROM
```bash
./extract_payload.sh path/to/xiaomi_15t_pro.zip
```

### Step 2 — Patch Build Props
```bash
./scripts/patch_props.sh
```

### Step 3 — Build Super Image
```bash
./scripts/build_super.sh
```

Full details in [`docs/build-guide.md`](docs/build-guide.md).

---

## 🐛 Known Issues

See [`docs/known-issues.md`](docs/known-issues.md) for full tracker.

**Critical:**
- Camera is completely non-functional — vendor HAL blobs from Infinix stock required
- Fingerprint sensor not recognized — Goodix HAL binary mismatch between Dimensity 1200 and 9400+
- `IHyperOSCustFeatureResolve` returns null — causes UI lag; stub service implementation pending
- MTK SODI deep idle disabled — battery drain higher than stock

**Minor:**
- Flashlight Quick Settings tile missing (overlay conflict)
- Some home screen widgets unavailable
- Certain HyperOS-exclusive settings pages may not render

---

## 📂 Repository Structure

```
.
├── README.md
├── CHANGELOG.md
├── LICENSE
├── docs/
│   ├── build-guide.md
│   ├── installation.md
│   └── known-issues.md
└── scripts/
    ├── patch_props.sh
    ├── build_super.sh
    └── extract_payload.sh
```

---

## 🙏 Credits

| Person / Project | Contribution |
|---|---|
| Xiaomi | HyperOS 3 source ROM |
| MIO-KITCHEN Team | ROM packing/editing tool |
| Infinix / Transsion | Stock vendor blobs |
| MediaTek | Dimensity platform |
| Android Open Source Project | AOSP base |

---

## ⚠️ Disclaimer

This ROM is provided **as-is** with no warranty. Flashing custom ROMs may void your warranty and carries a risk of bricking your device. The maintainer is not responsible for any damage. Proceed at your own risk.

---

## 📬 Contact

- Telegram: `@alan_achuz'
- GitHub Issues: [Open an issue](../../issues)

---

<div align="center">
Made with ❤️ and too many <code>logcat</code> sessions
</div>
```

---
