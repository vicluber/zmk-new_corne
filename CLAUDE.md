# ZMK Corne Keyboard Configuration Documentation

This file documents all the customizations and configurations made to the ZMK Corne keyboard setup.

## Project Overview

This is a custom ZMK firmware configuration for an Eyelash Corne keyboard with:
- 6-layer layout with specialized functions
- Rotary encoder support with scroll functionality
- RGB underglow with custom controls
- Mouse and pointing device support
- Custom layer-tap behaviors for improved responsiveness

## Layer Configuration

### Layer 0 (QWERTY) - Base Layer
- **Purpose**: Standard typing with QWERTY layout
- **Special Features**:
  - Arrow keys integrated in thumb cluster area (UP, LEFT/DOWN/RIGHT)
  - Custom tap-dance behavior (td0) for Shift/Caps Lock
  - Layer-tap behaviors with improved timing for spacebar responsiveness

### Layer 1 (NUMBER) - Numbers & Navigation
- **Purpose**: Numeric input and navigation
- **Layout**:
  - Top row: Numbers 1-9, 0
  - Navigation keys and function access
  - Bluetooth profile selection (BT_SEL 0-3)
  - RGB controls (RGB_OFF, RGB_ON, RGB_EFF, RGB_EFR, RGB_SPI, RGB_BRI, RGB_BRD)
  - Mouse movement controls in center area

### Layer 2 (SYMBOL) - Special Characters
- **Purpose**: Symbol input and output switching
- **Key Features**:
  - Standard symbol keys (!@#$%^&*())
  - Output switching: OUT_USB, OUT_BLE
  - Mouse controls (clicks and movement)
  - Additional symbols and brackets

### Layer 3 (Fn) - Function Keys & System
- **Purpose**: Function keys and system controls
- **Key Features**:
  - **studio_unlock** (top-left) - Enables ZMK Studio editing capabilities
  - Function keys F1-F12
  - System controls: bootloader, sys_reset
  - Mouse controls and movement
  - Print Screen, Scroll Lock, Pause/Break

### Layer 4 - Cursor & Mouse Controls
- **Purpose**: Dedicated cursor and mouse control layer
- **Layout** (swapped for ergonomics):
  - **Left side**: Arrow keys (UP_ARROW, LEFT_ARROW, DOWN_ARROW, RIGHT_ARROW)
  - **Right side**: Mouse controls (RCLK, MOVE_UP, LCLK, SCRL_UP, MOVE_LEFT, MOVE_DOWN, MOVE_RIGHT, SCRL_DOWN)

### Layer 5 (BT/HW) - Bluetooth & Hardware Controls
- **Purpose**: Complete hardware and system management
- **Left Side - Bluetooth Controls**:
  - **studio_unlock** (easy access)
  - Bluetooth profiles: BT_SEL 0, BT_SEL 1, BT_SEL 2, BT_SEL 3, BT_SEL 4
  - Bluetooth management: BT_CLR (clear current), BT_CLR_ALL (clear all)
- **Right Side - Hardware & RGB**:
  - Output switching: OUT_USB, OUT_BLE
  - System controls: bootloader, sys_reset
  - RGB controls: RGB_ON, RGB_OFF, RGB_BRI, RGB_BRD, RGB_EFF, RGB_EFR, RGB_SPI
- **Encoder**: RGB brightness control via rgb_encoder

## Custom Behaviors

### Layer-Tap Optimization (lt_space)
- **Problem Solved**: Spacebar lag when using layer-tap behaviors
- **Solution**: Custom hold-tap behavior with improved timing:
  ```
  tapping-term-ms = <300>;    // Increased from 200ms
  quick-tap-ms = <175>;       // Allow rapid successive taps  
  flavor = "tap-preferred";   // Prioritize tap over hold
  ```
- **Usage**: Replaces standard `&lt` for space keys (`&lt_space 2 SPACE`, `&lt_space 3 SPACE`)

### Tap-Dance (td0)
- **Purpose**: Shift/Caps Lock on single key
- **Behavior**: Tap for Left Shift, double-tap for Caps Lock

## Hardware Features

### Rotary Encoder Support
- **Scroll Encoder**: Configured for scrolling (SCRL_DOWN/SCRL_UP)
- **RGB Encoder**: Brightness control (RGB_BRI/RGB_BRD)
- **Volume Encoder**: Default layer volume control

### RGB Underglow
- **Configuration**: Located in `eyelash_corne.conf`
- **Settings**:
  - Enabled: `CONFIG_ZMK_RGB_UNDERGLOW=y`
  - Start state: OFF (`CONFIG_ZMK_RGB_UNDERGLOW_ON_START=n`)
  - Auto-off when idle: Enabled
  - Default hue: 160, Effect: 3
- **Controls**: Available in layers 1, 2, and 5

### Mouse/Pointing Device
- **Configuration**: `CONFIG_ZMK_POINTING=y`
- **Features**: Mouse movement, clicks, and scroll
- **Smooth scrolling**: Enabled
- **Custom scaling**: 2x horizontal, 1x vertical

## Key Mappings Reference

### Special Keys Explained
- **studio_unlock**: Enables full ZMK Studio editing when connected via USB
- **OUT_USB/OUT_BLE**: Switches keyboard output between USB (wired) and Bluetooth (wireless)
- **bootloader**: Enters bootloader mode for firmware updates
- **sys_reset**: Resets the keyboard system
- **BT_SEL 0-4**: Select Bluetooth profile (supports 5 different connections)
- **BT_CLR**: Clear current Bluetooth connection
- **BT_CLR_ALL**: Clear all stored Bluetooth connections

### Combo Keys
- **Backspace Combo 1**: Keys 23+24 → Backspace
- **Backspace Combo 2**: Keys 16+17 → Backspace

## Build & Development Notes

### GitHub Actions
- **Build Workflow**: Automated firmware building for left and right halves
- **Draw Workflow**: Initially enabled, later disabled due to parsing issues
- **Manual Drawing**: Instructions provided for local keymap visualization

### Configuration Files
- **Main Keymap**: `config/eyelash_corne.keymap`
- **Board Config**: `config/eyelash_corne.conf`
- **Drawer Config**: `keymap_drawer.config.yaml` (for visual keymap generation)

### Known Issues & Solutions
1. **Spacebar Lag**: Solved with custom `lt_space` behavior
2. **Drawing Failures**: Fixed key count mismatches between layers
3. **RGB Not Visible**: Configuration issue (start state was OFF)
4. **Build Failures**: Resolved devicetree syntax errors

## Manual Keymap Drawing (Draw Action Disabled)

Since automatic keymap drawing was disabled due to parsing issues:

### Option 1: Online Tool
1. Visit [keymap-drawer web tool](https://caksoylar.github.io/keymap-drawer/)
2. Upload `config/eyelash_corne.keymap`
3. Optionally upload `keymap_drawer.config.yaml` for styling

### Option 2: Local Installation
```bash
pip install keymap-drawer
keymap parse -c keymap_drawer.config.yaml -z config/eyelash_corne.keymap > keymap.yaml
keymap draw keymap.yaml > keymap.svg
```

## Firmware Features Summary

✅ **6-layer layout** with specialized functions  
✅ **Improved spacebar responsiveness** with custom timing  
✅ **Complete bluetooth management** (5 profiles + clearing)  
✅ **Hardware controls** (bootloader, reset, studio access)  
✅ **RGB underglow** with comprehensive controls  
✅ **Mouse/pointing support** with smooth scrolling  
✅ **Rotary encoder** for volume and RGB control  
✅ **Output switching** between USB and Bluetooth  
✅ **Ergonomic cursor/mouse** layout in layer 4  

## Usage Tips

1. **Layer 5 Access**: Use `&lt 5 RIGHT_ALT` for hardware controls
2. **Spacebar Layers**: `&lt_space 2 SPACE` and `&lt_space 3 SPACE` for symbols/functions
3. **Studio Access**: Press studio_unlock in layer 3 or 5 before using ZMK Studio
4. **Bluetooth Switching**: Use layer 5 for profile management and output switching
5. **RGB Control**: Available in multiple layers (1, 2, 5) for convenience
6. **Mouse Control**: Layer 4 provides dedicated cursor and mouse functionality

## Configuration Goals Achieved

- ✅ Organized bluetooth and hardware controls in Layer 5
- ✅ Consistent cursor vs mouse control placement across layers  
- ✅ Easy access to studio_unlock for configuration changes
- ✅ Optimized layer-tap behavior for smooth typing experience
- ✅ Comprehensive RGB control across multiple layers
- ✅ Ergonomic layout with logical key groupings