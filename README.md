# ZMK Corne Keyboard Configuration

A custom ZMK firmware configuration for the **Eyelash Corne** keyboard with advanced features including 6-layer layout, rotary encoder support, RGB underglow, and mouse controls.

![Eyelash Corne Keyboard](https://ae01.alicdn.com/kf/Sa797fee25edd44248fbfdb0e13d44e00B.jpg)

**⚠️ Important:** This keyboard is different from [foostan's Corne](https://github.com/foostan/crkbd) and is **not compatible** with standard `corne` firmware.

## ✨ Features

- **6-layer layout** with specialized functions for different use cases
- **Improved spacebar responsiveness** with custom layer-tap timing
- **Complete Bluetooth management** - 5 profiles with easy switching
- **RGB underglow** with comprehensive controls across multiple layers
- **Mouse/pointing device support** with smooth scrolling
- **Rotary encoder support** for volume and RGB brightness control
- **Hardware controls** (bootloader access, system reset, ZMK Studio unlock)
- **Output switching** between USB (wired) and Bluetooth (wireless)

## 🚀 Quick Start

### For New Users
1. [Fork this repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo#forking-a-repository)
2. [Enable GitHub Actions](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/disabling-and-enabling-a-workflow#enabling-a-workflow) in the Actions tab
3. Wait for the build to complete and download your firmware files
4. Flash the firmware to your keyboard halves

### For Existing ZMK Users
If you already have a ZMK configuration repository, you can [add this as a module](https://zmk.dev/docs/features/modules#building-with-modules) instead of forking.

## 📋 Layer Layout

### Layer 0 (QWERTY) - Base Layer
Standard QWERTY typing with integrated arrow keys and custom behaviors:
- **Arrow keys** in thumb cluster area
- **Shift/Caps Lock** tap-dance behavior
- **Optimized spacebar** with improved layer-tap responsiveness

### Layer 1 (NUMBER) - Numbers & Navigation
- Numbers 1-9, 0 on top row
- Bluetooth profile selection (BT_SEL 0-3)
- RGB controls (on/off, effects, brightness)
- Mouse movement controls

### Layer 2 (SYMBOL) - Special Characters
- Standard symbols (!@#$%^&*())
- Output switching (USB/Bluetooth)
- Mouse controls (clicks and movement)
- Additional brackets and symbols

### Layer 3 (Fn) - Function Keys & System
- **ZMK Studio unlock** (top-left) - enables configuration editing
- Function keys F1-F12
- System controls (bootloader, reset)
- Print Screen, Scroll Lock, Pause/Break

### Layer 4 - Cursor & Mouse Controls
Dedicated cursor and mouse control with ergonomic layout:
- **Left side:** Arrow keys (↑←↓→)
- **Right side:** Mouse controls (clicks, movement, scroll)

### Layer 5 (BT/HW) - Bluetooth & Hardware
Complete hardware and system management:
- **Bluetooth:** 5 profiles, clear current/all connections
- **Hardware:** Bootloader, system reset, ZMK Studio unlock
- **RGB:** Full control suite (on/off, brightness, effects)
- **Output:** USB/Bluetooth switching

## 🎛️ Hardware Configuration

### Rotary Encoder
- **Default layer:** Volume control
- **Layer 5:** RGB brightness control
- **Scroll mode:** Page up/down functionality

### RGB Underglow
- **Start state:** OFF (prevents accidental activation)
- **Auto-off:** When keyboard is idle
- **Controls:** Available in layers 1, 2, and 5
- **Effects:** Multiple lighting patterns available

### Mouse/Pointing Device
- **Smooth scrolling** enabled
- **Custom scaling:** 2x horizontal, 1x vertical movement
- **Full control:** Movement, clicks, and scroll in multiple layers

## 🔧 Key Features Explained

| Key | Function |
|-----|----------|
| `studio_unlock` | Enables ZMK Studio for configuration editing (USB connection required) |
| `OUT_USB/OUT_BLE` | Switch between wired (USB) and wireless (Bluetooth) output |
| `bootloader` | Enter bootloader mode for firmware updates |
| `sys_reset` | Reset keyboard system |
| `BT_SEL 0-4` | Select Bluetooth profile (supports 5 different devices) |
| `BT_CLR` | Clear current Bluetooth connection |
| `BT_CLR_ALL` | Clear all stored Bluetooth connections |

## 📱 Usage Tips

1. **Hardware Controls:** Access Layer 5 with `Right Alt + hold` for all system functions
2. **Spacebar Layers:** Use spacebar + hold to access symbols (Layer 2) and functions (Layer 3)
3. **ZMK Studio:** Press `studio_unlock` before connecting ZMK Studio for configuration
4. **Bluetooth Management:** Use Layer 5 for switching profiles and managing connections
5. **RGB Control:** Available in multiple layers (1, 2, 5) for convenient access
6. **Mouse Mode:** Layer 4 provides dedicated cursor and mouse functionality

## 🛠️ Building Firmware

The firmware builds automatically via GitHub Actions when you push changes. Download the built firmware files from the Actions tab.

### Manual Build (Advanced)
```bash
# Clone with west
west init -l config
west update
west build -p -d build/left -b eyelash_corne_left
west build -p -d build/right -b eyelash_corne_right
```

## 🎨 Keymap Visualization

### Generate Keymap Diagram
Since automatic drawing is disabled, use these options:

**Option 1: Online Tool**
1. Visit [keymap-drawer web tool](https://caksoylar.github.io/keymap-drawer/)
2. Upload `config/eyelash_corne.keymap`
3. Optionally upload `keymap_drawer.config.yaml` for styling

**Option 2: Local Installation**
```bash
pip install keymap-drawer
keymap parse -c keymap_drawer.config.yaml -z config/eyelash_corne.keymap > keymap.yaml
keymap draw keymap.yaml > keymap.svg
```

## 🔄 Configuration Updates

All customizations and modifications are documented in `CLAUDE.md`. This includes:
- Layer configurations and purposes
- Custom behavior explanations
- Hardware feature settings
- Troubleshooting solutions

## 📞 Support

- **3D Models:** Contact `380465425@qq.com` for keyboard 3D models
- **ZMK Documentation:** [Official ZMK Docs](https://zmk.dev/)
- **Issues:** Use GitHub Issues for configuration problems

## 🏆 Configuration Goals Achieved

- ✅ Organized bluetooth and hardware controls in Layer 5
- ✅ Consistent cursor vs mouse control placement
- ✅ Easy access to ZMK Studio unlock
- ✅ Optimized layer-tap behavior for smooth typing
- ✅ Comprehensive RGB control across multiple layers
- ✅ Ergonomic layout with logical key groupings

---

*This configuration is specifically designed for the Eyelash Corne keyboard and includes optimizations for daily productivity use with advanced hardware features.*