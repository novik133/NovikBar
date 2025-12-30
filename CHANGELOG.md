# Changelog

All notable changes to NovaBar will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2025-12-30

### Added
- Initial release of NovaBar
- macOS-style panel for Linux (X11/XFCE)
- Global menu integration with GTK applications
- Logo menu with system actions (About, Settings, Sleep, Restart, Shutdown)
- System indicators:
  - Network status with NetworkManager integration
  - Bluetooth connectivity indicator
  - Sound/volume control
  - Battery status and charging indicator
  - Date and time display
  - Notification center
  - Control center for quick settings
- Settings panel with theme customization
- Dark and light theme support
- CSS-based styling system
- X11 strut reservation for proper panel positioning
- About dialog with application information
- Modular architecture for easy extension
- Meson build system integration
- Auto-start desktop entry support

### Technical Features
- Built with Vala and GTK3
- libwnck integration for window management
- D-Bus communication for global menus
- NetworkManager (libnm) integration
- X11 window system compatibility
- appmenu-gtk-module support

[0.1.0]: https://github.com/novik133/NovikBar/releases/tag/v0.1.0
