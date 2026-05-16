# SamRevert

A modern, dark-themed graphical user interface (GUI) built with CustomTkinter for safely managing and executing Samsung firmware downgrades. This tool provides a wizard-style step flow to guide you through device detection, firmware selection, safety verifications, and flashing.

## Features

- **Device Detection**: Automatic identification of connected devices using standard communication interfaces.
- **Firmware Selection**: Seamless loading and verification of target firmware packages.
- **Pre-flight Safety Checks**: Built-in logic to analyze target configurations, inspect software versions, and evaluate safety before proceeding.
- **Download Management**: Handles necessary resource downloads required for the environment.
- **Flash Execution**: Controlled execution interface for flashing firmware packages securely.

## Project Structure

```text
samsung_downgrader/
├── core/
│   ├── adb_manager.py          # Device detection, info reading, and control
│   ├── rollback_checker.py    # Firmware string parsing and downgrade safety analysis
│   ├── safety_checks.py       # Pre-flight system validations
│   └── heimdall_manager.py    # Interface wrapper for flash execution
├── ui/
│   └── main_gui.py            # Main application interface built with CustomTkinter
└── logo.ico                   # Application icon asset
```

## Prerequisites

To run the source code directly, you need Python 3.10+ and the required packages installed:

```bash
pip install customtkinter pyinstaller
```

## Running the Application

To run the GUI interface directly from source:

```bash
python ui/main_gui.py
```

## Compilation (Building Standalone .exe)

To bundle the entire tool into a single standalone executable file (`.exe`) with your custom icon embedded, use the following PyInstaller command from the root directory:

```bash
python -m PyInstaller --clean --noconfirm --onefile --windowed --icon="logo.ico" --collect-all customtkinter --add-data "core;core" --add-data "firmware;firmware" --add-data "ui;ui" ui/main_gui.py
```

Once the compilation process completes, the final executable will be located in the `dist/` directory:
- `dist/main_gui.exe`

## Usage Guide

1. **Launch**: Open `main_gui.exe`.
2. **Connect**: Connect your target device via USB and ensure correct interface settings are active.
3. **Select Firmware**: Browse and load the appropriate firmware package for your specific hardware variant.
4. **Safety Check**: Run the pre-flight verification step to ensure rollback parameters match acceptable boundaries.
5. **Flash**: Proceed to the final execution step to apply the firmware updates safely.

## License

This project is intended for educational and maintenance purposes. Ensure compliance with specific hardware guidelines and software terms when administering system updates.
