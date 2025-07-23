# Installing Git

Before we can start using Git, we need to install it on your system. This guide covers installation for Windows, macOS, and Linux.

## Check if Git is Already Installed

First, let's check if you already have Git installed on your system:

```bash
git --version
```

If Git is installed, you'll see output like:
```
git version 2.40.1
```

If Git is not installed, you'll see an error message, and you'll need to install it using the instructions below.

## Installation by Operating System

### Windows 🪟

1. **Download Git for Windows**
   - Visit the official Git website: [https://git-scm.com/download/win](https://git-scm.com/download/win)
   - Click the "Download" button to get the latest version

2. **Run the Installer**
   - Run the downloaded `.exe` file
   - Follow the installation wizard with recommended settings
   - **Important**: Git for Windows includes **Git Bash**, which provides a Linux-like terminal environment

3. **Verify Installation**
   - Open Command Prompt, PowerShell, or Git Bash
   - Run `git --version` to confirm installation

!!! tip "Git Bash Recommendation"
    Git Bash provides a consistent command-line experience across different operating systems. It's especially useful if you're learning Git commands that work the same way on Linux and macOS.

### macOS 🍎

#### Option 1: Download from Official Website
1. Visit [https://git-scm.com/download/mac](https://git-scm.com/download/mac)
2. Download the installer for your macOS version
3. Run the installer and follow the instructions

#### Option 2: Using Homebrew (Recommended)
If you have Homebrew installed:

```bash
brew install git
```

#### Option 3: Using Xcode Command Line Tools
Git comes bundled with Xcode Command Line Tools:

```bash
xcode-select --install
```

### Linux 🐧

The installation method depends on your Linux distribution:

#### Ubuntu/Debian
```bash
sudo apt update
sudo apt install git
```

#### Fedora
```bash
sudo dnf install git
```

#### CentOS/RHEL
```bash
sudo yum install git
```

#### Arch Linux
```bash
sudo pacman -S git
```

## Verify Your Installation

After installation, verify that Git is working correctly:

```bash
# Check Git version
git --version

# Check Git help (optional)
git help
```

You should see:
- The Git version number
- Help information if you run `git help`

## Troubleshooting Installation Issues

### Command Not Found
If you get a "command not found" error:

1. **Restart your terminal** after installation
2. **Check your PATH**: Make sure Git's installation directory is in your system PATH
3. **Reinstall Git** following the instructions above

### Permission Issues (Linux/macOS)
If you encounter permission issues:

```bash
# Check if git is executable
which git

# If needed, make it executable
chmod +x /usr/local/bin/git
```

### Windows-Specific Issues
- Make sure you're using the correct terminal (Command Prompt, PowerShell, or Git Bash)
- Try running as Administrator if you encounter permission issues
- Verify that Git was added to your system PATH during installation

## Next Steps

Great! Now that you have Git installed, let's move on to [configuring Git](configuration.md) for first-time use.

---

!!! question "Still Having Issues?"
    If you're still having trouble with installation, check our [troubleshooting guide](../advanced/troubleshooting.md) or consult the [official Git documentation](https://git-scm.com/doc).
