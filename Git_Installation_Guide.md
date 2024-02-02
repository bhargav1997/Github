# Steps for installing Git on macOS, Windows, and Linux using the command line:

### Installation Steps:

#### **macOS:**

1. Open Terminal.
2. Install Homebrew (if not installed):
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
3. Install Git using Homebrew:
   ```bash
   brew install git
   ```

#### **Windows:**

1. Download the Git for Windows installer from [Git official website](https://gitforwindows.org/).
2. Run the installer and follow the installation steps.
3. Open Git Bash to verify the installation:
   ```bash
   git --version
   ```

#### **Linux:**

##### **Ubuntu/Debian:**

1. Open Terminal.
2. Update package list:
   ```bash
   sudo apt update
   ```
3. Install Git:
   ```bash
   sudo apt install git
   ```

##### **Fedora:**

1. Open Terminal.
2. Install Git:
   ```bash
   sudo dnf install git
   ```

##### **Arch Linux:**

1. Open Terminal.
2. Install Git:
   ```bash
   sudo pacman -S git
   ```

#### **Verify Installation:**

To verify the installation on any platform, open a new terminal/command prompt and run:
```bash
git --version
```

This should display the installed Git version.
