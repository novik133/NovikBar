# NovaBar

A modern, modular macOS-style panel for Linux (X11/XFCE) built with Vala and GTK3.

![NovaBar Screenshot](Screenshots/1.png)

## Features

### Core Components
- **Global Menu Bar** - Application menus integrated into the panel (like macOS)
- **Logo Menu** - System actions menu with Nova branding
- **System Indicators** - Network, Bluetooth, Sound, Battery, DateTime, Notifications
- **Control Center** - Quick access to system settings
- **Settings Panel** - Theme customization and configuration

### Key Features
- **macOS-style Design** - Clean, modern interface with transparency effects
- **Global Menu Integration** - Application menus appear in the panel instead of windows
- **System Tray Replacement** - Modern indicators replace traditional system tray
- **Theme Support** - Dark and light themes with CSS customization
- **X11 Integration** - Proper window management and strut reservation
- **Modular Architecture** - Easy to extend with new indicators and components

## Screenshots

| Feature | Screenshot |
|---------|------------|
| Main Panel | ![Main](Screenshots/1.png) |
| Global Menu | ![Menu](Screenshots/2.png) |
| Global Menu2 | ![Menu2](Screenshots/3.png) |
| Indicators | ![Indicators](Screenshots/4.png) |
| Logo Menu | ![Logo](Screenshots/5.png) |

## Requirements

### System Dependencies
- GTK+ 3.0
- GLib 2.0
- GIO 2.0
- GDK X11 3.0
- libwnck 3.0
- X11
- NetworkManager (libnm)

### Build Dependencies
- Vala compiler
- Meson build system
- Ninja build tool
- pkg-config

### Runtime Requirements
- X11 window system
- XFCE or compatible desktop environment
- appmenu-gtk-module (for global menu support)

## Installation

### From Source

1. **Install dependencies** (Ubuntu/Debian):
```bash
sudo apt install valac meson ninja-build pkg-config \
    libgtk-3-dev libglib2.0-dev libgio2.0-dev \
    libgdk-x11-3.0-dev libwnck-3-dev libx11-dev \
    libnm-dev appmenu-gtk-module
```

2. **Clone and build**:
```bash
git clone https://github.com/novik133/NovikBar.git
cd NovaBar
meson setup build
ninja -C build
```

3. **Install**:
```bash
sudo ninja -C build install
```

4. **Run**:
```bash
novabar
```

### Auto-start Setup

Create desktop entry for auto-start:
```bash
mkdir -p ~/.config/autostart
cat > ~/.config/autostart/novabar.desktop << EOF
[Desktop Entry]
Type=Application
Name=NovaBar
Exec=novabar
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
EOF
```

## Configuration

### Global Menu Setup

For applications to show menus in the panel:

1. **Install appmenu support**:
```bash
sudo apt install appmenu-gtk2-module appmenu-gtk3-module
```

2. **Set environment variables**:
```bash
export UBUNTU_MENUPROXY=1
export APPMENU_DISPLAY_BOTH=1
```

Add to `~/.profile` or `~/.xsessionrc` for persistence.

### Theme Customization

NovaBar includes two built-in themes:
- **Dark Theme** (`novaos.css`) - Default dark theme
- **Light Theme** (`novaos-light.css`) - Light variant

Themes are installed to `/usr/share/novaos/` and can be customized via the Settings panel.

## Project Structure

```
NovaBar/
├── src/
│   ├── main.vala              # Application entry point
│   ├── panel.vala             # Main panel window and layout
│   ├── globalmenu/            # Global menu integration
│   │   ├── menubar.vala       # GTK global menu widget
│   │   └── README.md          # Global menu documentation
│   ├── logomenu/              # Nova logo menu
│   │   ├── logomenu.vala      # System actions menu
│   │   └── README.md          # Logo menu documentation
│   ├── indicators/            # System indicators
│   │   ├── network/           # Network status indicator
│   │   ├── bluetooth/         # Bluetooth indicator
│   │   ├── sound/             # Volume control
│   │   ├── battery/           # Battery status
│   │   ├── datetime/          # Clock and calendar
│   │   ├── notifications/     # Notification center
│   │   └── controlcenter/     # Quick settings
│   ├── settings/              # Configuration interface
│   │   └── settings.vala      # Settings window
│   └── about/                 # About dialog
│       └── about.vala         # Application information
├── data/
│   ├── novaos.css             # Dark theme stylesheet
│   └── novaos-light.css       # Light theme stylesheet
├── Screenshots/               # Application screenshots
├── meson.build                # Build configuration
├── LICENCE.md                 # GPL-3.0 license
└── README.md                  # This file
```

## Development

### Building for Development

```bash
meson setup build --buildtype=debug
ninja -C build
./build/novabar
```

### Adding New Indicators

1. Create new directory in `src/indicators/`
2. Implement indicator class extending appropriate base
3. Add to `meson.build` sources
4. Register in `panel.vala` right_box

### Code Style

- Follow Vala conventions
- Use 4-space indentation
- Document public APIs
- Maintain modular architecture

## Troubleshooting

### Global Menu Not Working
- Ensure `appmenu-gtk-module` is installed
- Check environment variables are set
- Restart applications after setup

### Panel Not Appearing
- Check X11 compatibility
- Verify dependencies are installed
- Run from terminal to see error messages

### High CPU Usage
- Check for window manager conflicts
- Disable other panels/docks
- Monitor system resources

## Contributing

1. Fork the repository
2. Create feature branch
3. Make changes following code style
4. Test thoroughly
5. Submit pull request

## License

GPL-3.0 - See [LICENCE](LICENCE) for details.

## Credits

- Built with Vala and GTK3
- Inspired by macOS design principles
- Uses libwnck for window management
- NetworkManager integration for network status

---

**NovaBar** - Bringing macOS-style elegance to Linux desktops.
