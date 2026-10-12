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

### Windows: Kernel crashes when plotting in Jupyter notebooks (Miniforge)

On Windows, selecting a Miniforge environment kernel in VS Code may attach the
Python interpreter without activating the environment. Because Miniforge does
not register in the Windows Registry, VS Code cannot locate `conda.exe`
automatically to run activation scripts. When executing cells that import
plotting libraries (such as `matplotlib`), missing `PATH` entries for native
dependencies cause the kernel to crash silently ("The kernel died"). Anaconda
users are typically unaffected because Anaconda registers standard system
paths during installation.

To verify whether your setup is affected, run a cell with:

```python
import matplotlib.pyplot as plt

plt.plot([1, 2], [1, 2])
plt.show()
```

If the kernel crashes, apply one of the following fixes:

#### Option 1: Set the Conda path in VS Code settings (recommended)

1. Open **Miniforge Prompt** (or **Anaconda Prompt**) from the Start menu.
2. Run the following command to print the path to `conda.exe`:
   ```cmd
   for /f "delims=" %i in ('conda info --base') do @echo %i\Scripts\conda.exe
   ```
   This prints a path such as:
   ```text
   C:\Users\<username>\AppData\Local\miniforge3\Scripts\conda.exe
   ```
3. Copy the output.
4. In VS Code, open Settings (**File > Preferences > Settings** or `Ctrl+,`).
5. Search for `python.condaPath`.
6. Paste the full path into the setting.
7. Restart VS Code.

#### Option 2: Launch VS Code from an activated Miniforge Prompt

If VS Code was added to `PATH` during installation:

1. Save your work and close all VS Code windows.
2. Open **Miniforge Prompt** from the Start menu.
3. Run:
   ```cmd
   conda activate TECH6
   code
   ```
Use this command each time you launch VS Code for the course.

#### Option 3: Reinstall Miniforge and enable PATH

1. Save your work and close VS Code.
2. Uninstall Miniforge, then reinstall it using the Windows installer.
3. During installation, check
   **Add Miniforge3 to my PATH environment variable for your user installation**.
4. Open a new Miniforge Prompt and recreate the `TECH6` environment:
   ```cmd
   conda env create -f environment.yml
   ```

## Python integration

- Read the Python-specific
  [quick start guide](https://code.visualstudio.com/docs/python/python-quick-start).
- VS Code comes with numerous useful Python extensions. You will be asked to install
  them when you open Python files or Jupyter notebooks for the first time.

