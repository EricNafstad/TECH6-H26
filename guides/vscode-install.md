# Installing Visual Studio Code (VS Code)

- VS Code is the core code editor used throughout the course.

## Installation & setup

### Download & install

- Website:
  [https://code.visualstudio.com/download](https://code.visualstudio.com/download)
- **Windows**: Download the Windows installer `.exe`. Run setup and accept default
  options.
- **macOS**: Download the Universal `.dmg` installer (works on Apple Silicon and
  Intel). Open the `.dmg` and drag VS Code to the `Applications` folder.
- **Linux**: Download the `.deb` or `.rpm` package for your distribution.

### Verification

- Launch VS Code from the Start Menu (Windows) or Applications / Spotlight (macOS).
  Confirm it opens to the Welcome tab.
- To check for updates, select **Help > Check for Updates...** (Windows/Linux) or
  **Code > Check for Updates...** (macOS).
- As of October 10, 2026, the latest version of VS Code is 1.141; make sure to have
  something similar.

### macOS: Cannot update on a read-only volume

If VS Code reports "Cannot update while running on a read-only volume", common causes
are running it from **Downloads**, directly from a mounted **`.dmg` disk image**, or
another quarantined/read-only location. The updater needs permission to modify the
application.

1. Quit VS Code completely (`Cmd+Q`).
2. In Finder, drag `Visual Studio Code.app` into **Applications** (`/Applications`)
   in the sidebar. If you opened a `.dmg`, drag the VS Code icon onto the
   **Applications** folder shown in that window. This copies the app onto your Mac.
3. Eject any mounted VS Code disk image from Finder's sidebar.
4. Launch the copy from `/Applications` and confirm that it opens successfully.
5. You can now delete the `.dmg` file from **Downloads**. It is only needed for
   installation; deleting it does not remove the installed app.
6. Remove any old Dock shortcut and add the copy from `/Applications`.
7. Select **Code > Check for Updates...** and retry.

## Configuring Conda environments in VS Code

### Python scripts (`.py`)

1. Open the project folder in VS Code.
2. Open the Command Palette (`Ctrl+Shift+P` on Windows/Linux, `Cmd+Shift+P` on macOS).
3. Search and select **Python: Select Interpreter**.
4. Select the desired environment (e.g., `Python 3.14 ('TECH6')`). This is verified
   via the status bar at the bottom.

### Jupyter notebooks (`.ipynb`)

1. Open a notebook file in VS Code.
2. Click **Select Kernel** in the top-right corner.
3. Choose **Python Environments...** and select the target environment (`TECH6`).
4. Requires the `ipykernel` package in the active environment (already included in
   the `TECH6` environment).

## Python integration

- Read the Python-specific
  [quick start guide](https://code.visualstudio.com/docs/python/python-quick-start).
- VS Code comes with numerous useful Python extensions. You will be asked to install
  them when you open Python files or Jupyter notebooks for the first time.
