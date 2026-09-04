# Meowncher Developer Guide

## Building Meowncher

### Prerequisites
- CMake 3.25+
- Qt 6.4+
- C++ 23 compiler (GCC 11+, Clang 14+, MSVC 2019+)
- vcpkg for dependency management
- Ninja build system

### Quick Start

```bash
# Install dependencies (Ubuntu/Debian)
sudo apt-get install cmake ninja-build qt6-base-dev qt6-tools-dev qt6-opengl-dev libgl1-mesa-dev

# Configure
cmake --preset linux

# Build (specific target)
cd build && ninja -j$(nproc) launcher

# Run
./meowncher
```

### Build Variants

```bash
# Debug build with more logging
cmake --preset linux -DCMAKE_BUILD_TYPE=Debug

# Release build with optimizations
cmake --preset linux -DCMAKE_BUILD_TYPE=Release

# With LTO enabled for smaller binary
cmake --preset linux -DENABLE_LTO=ON
```

## Project Structure

```
├── CMakeLists.txt              # Main build configuration
├── program_info/               # Branding and metadata
│   ├── CMakeLists.txt         # Branding configuration
│   ├── org.meowncher.Meowncher.desktop.in
│   ├── org.meowncher.Meowncher.metainfo.xml.in
│   └── *.svg, *.ico           # Icons and assets
├── launcher/                   # Main application code
│   ├── Application.cpp/h      # Main app class
│   ├── main.cpp               # Entry point
│   ├── ui/                    # UI components
│   │   ├── MainWindow.cpp/h/ui
│   │   ├── dialogs/           # Dialog implementations
│   │   ├── pages/             # Settings pages
│   │   ├── instanceview/      # Instance list UI
│   │   ├── themes/            # Theme implementations
│   │   └── widgets/           # Reusable widgets
│   ├── minecraft/             # Minecraft integration
│   ├── modplatform/           # Mod platform integrations
│   ├── java/                  # Java detection/management
│   ├── settings/              # Settings storage
│   └── tasks/                 # Long-running tasks
├── libraries/                  # Internal libraries
│   ├── launcher/              # Launcher library
│   ├── qdcss/                 # CSS processing
│   └── rainbow/               # Color utilities
└── tests/                      # Unit tests
```

## Key Classes

### Application Core
- `Application`: Main QApplication subclass, handles initialization
- `MainWindow`: Primary UI window
- `InstanceList`: Manages loaded instances
- `BaseInstance`: Base class for instances

### UI Components
- `InstanceView`: Lists instances
- `InstanceDelegate`: Renders individual instances
- `LauncherPage`: Main launcher interface

### Configuration
- `BuildConfig`: Generated during build with version/branding info
- `Settings` (in settings/): Persistent application settings

## Branding Configuration

All branding is controlled in `program_info/CMakeLists.txt`:

```cmake
set(Launcher_CommonName "Meowncher")
set(Launcher_DisplayName "Meowncher")
set(Launcher_AppID "org.meowncher.Meowncher")
set(Launcher_Domain "meowncher.local")
set(Launcher_ENVName "MEOWNCHER")
```

When modified, rebuild to regenerate:
- Application title and window titles
- About dialog content
- Desktop files and metadata
- Application icons and IDs

## Code Style

### C++ Guidelines
- Use modern C++23 features
- Follow RAII principles
- Use smart pointers (std::unique_ptr, std::shared_ptr)
- Use Qt memory management for QObjects
- Avoid raw pointers when possible

### Naming Conventions
- Classes: PascalCase (MainWindow, InstanceView)
- Functions/methods: camelCase (getVersion, setAttribute)
- Constants: UPPER_SNAKE_CASE (MAX_INSTANCES, DEFAULT_TIMEOUT)
- Member variables: camelCase with m_ prefix (m_instanceList, m_settings)
- File names: match class names (MainWindow.cpp, MainWindow.h)

### Copyright Headers
Always include copyright headers:
```cpp
// SPDX-License-Identifier: GPL-3.0-only
/*
 *  Meowncher - Minecraft Launcher
 *  Copyright (C) 2025 [Your Name/Contribution]
 *
 *  This program is free software...
 */
```

## Making UI Changes

### To Change Window Titles
Edit Application.cpp or configure BuildConfig variables - titles are set automatically.

### To Change User-Facing Strings
1. Find the string in the source or .ui file
2. Wrap in `tr()` if not already wrapped
3. Rebuild to update

### To Update Dialogs
1. Edit the .ui file in `launcher/ui/dialogs/` using Qt Designer
2. Or edit the C++ code directly
3. Rebuild

### To Modify Themes
1. Edit theme class in `launcher/ui/themes/`
2. Themes inherit from ITheme
3. Implement colorScheme(), appStyleSheet(), etc.

### To Add Settings
1. Add setting key in application/settings configuration
2. Create UI in settings page (.ui file or code)
3. Connect to Settings class
4. Implement save/load logic

## Testing

### Run Tests
```bash
cd build
ctest
```

### Manual Testing Checklist
- [ ] Application launches
- [ ] Can create new instance
- [ ] Can launch instance
- [ ] Settings persist
- [ ] Themes switch properly
- [ ] Window resizing works
- [ ] Right-click context menus work
- [ ] Keyboard navigation works

## Debugging

### Enable Debug Output
```bash
export QT_DEBUG_PLUGINS=1
./meowncher -l launcher.org.meowncher.Meowncher
```

### Qt Creator Debugging
- Open project in Qt Creator
- Configure build kit for Qt 6
- Set breakpoints and run with debugger

### Qt Designer
Edit .ui files:
```bash
designer launcher/ui/MainWindow.ui
```

## Performance Tips

### Profiling
Use Qt Creator's built-in profiler:
- Tools → Analyzer → QML Profiler
- Tools → Analyzer → Performance Analyzer

### Common Optimizations
- Virtualize lists with many items
- Cache frequently accessed data
- Avoid layout recalculations
- Use QPixmapCache for icons
- Profile before and after changes

## Git Workflow

### Commit Messages
```
Short description (50 chars)

Longer description explaining:
- What changed
- Why it changed
- Any relevant issue numbers

Fixes #123
```

### Branch Naming
- `feature/instance-search` - New features
- `fix/crash-on-launch` - Bug fixes
- `refactor/ui-components` - Code improvements
- `docs/api-guide` - Documentation

## Translations

Translatable strings use `tr()`:
```cpp
QPushButton *button = new QPushButton(tr("Launch Instance"));
```

Translations are managed through Weblate or translation files.

## Resources & Documentation

### Qt Documentation
- Qt Core: https://doc.qt.io/qt-6/qtcore-index.html
- Qt GUI: https://doc.qt.io/qt-6/qtgui-index.html
- Qt Widgets: https://doc.qt.io/qt-6/qtwidgets-index.html

### CMake
- CMake Documentation: https://cmake.org/documentation/

### Minecraft
- Launcher Wrapper: https://github.com/PrismLauncher/launchwrapper
- Authentication: Yggdrasil/Microsoft Graph API

### Contributing
See CONTRIBUTING.md for full guidelines

## Common Issues & Solutions

### Build fails with Qt not found
```bash
# Set Qt path
export CMAKE_PREFIX_PATH=/path/to/qt/gcc_64/lib/cmake
```

### Icons not showing
- Rebuild to regenerate icon resources
- Check that .qrc file is properly configured
- Verify icon paths are correct

### Settings not persisting
- Check Settings class for proper serialization
- Verify file permissions
- Check config directory existence

### UI looks wrong
- Verify theme is loading
- Check stylesheet syntax
- Test in different themes

## Additional Resources

- Prism Launcher Repository: https://github.com/PrismLauncher/PrismLauncher
- Qt Documentation: https://doc.qt.io
- MultiMC (predecessor): https://github.com/MultiMC/MultiMC5

## Getting Help

- GitHub Issues: Report bugs and feature requests
- Discussions: Ask questions and discuss
- Discord: Community support
- Matrix: Community space
