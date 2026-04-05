![Windows Compatibility](https://img.shields.io/badge/Windows-10%2B-blue)
![Linux Compatibility](https://img.shields.io/badge/Linux-Fedora%2FUbuntu-yellow)
![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)

# CoomerDL

**CoomerDL** is a powerful cross-platform desktop application for downloading media content (images, videos, documents, and compressed files) from supported adult content websites. Built with Python and PySide6, it provides a modern, intuitive graphical interface with advanced features like multithreaded downloads, progress tracking, and customizable download management.

## Table of Contents

- [Key Features](#key-features)
- [Supported Sites](#supported-sites)
- [Supported File Types](#supported-file-types)
- [Tech Stack](#tech-stack)
- [Screenshots](#screenshots)
- [Installation](#installation)
  - [Windows](#1-windows)
  - [Linux (Ubuntu/Debian)](#2-linux-ubuntudebian)
  - [Linux (Fedora/RHEL)](#3-linux-fedorarhel)
  - [macOS](#4-macos)
- [Running the Application](#running-the-application)
- [Configuration](#configuration)
  - [Download Settings](#download-settings)
  - [File Naming Modes](#file-naming-modes)
  - [Folder Structure](#folder-structure)
- [SimpCity Cookies](#simpcity-cookies)
- [Download Database](#download-database)
- [Logs](#logs)
- [Language Support](#language-support)
  - [How Translations Work](#how-translations-work)
  - [Adding a New Language](#adding-a-new-language-in-a-fork)
- [Fork Guide](#fork-guide)
- [Troubleshooting](#troubleshooting)
  - [Common Issues](#common-issues)
  - [Getting Help](#getting-help)
- [CLI Alternatives](#cli-alternatives)
- [Support](#support)
- [License](#license)

---

## Key Features

- **Modern PySide6 Interface** — Clean, native-looking desktop application with dark/light theme support
- **Multi-site Support** — Download from Coomer, Kemono, Erome, Bunkr, SimpCity, and JPG5
- **Multithreaded Downloads** — Configurable concurrent download limits (1-20 workers)
- **Progress Tracking** — Per-file and global progress with speed and ETA display
- **Resume Capability** — Automatic retry with configurable attempts and intervals
- **Duplicate Prevention** — SQLite database tracks downloaded files to avoid re-downloading
- **Flexible Naming** — Four file naming modes to suit different organization preferences
- **Custom Folder Structure** — Organize downloads by user, file type, or post
- **Cookie Support** — Built-in cookie management for sites requiring authentication (SimpCity)
- **Logging** — Exportable logs with domain-aware formatting for easy debugging
- **Internationalization** — English and Spanish included by default, extensible translation system

---

## Supported Sites

| Site | URL | Status |
|------|-----|--------|
| Coomer | `https://coomer.su` | ✅ Active |
| Coomer (alternate) | `https://official.coomer.com.co` | ✅ Active |
| Kemono | `https://kemono.su` | ✅ Active |
| Erome | `https://www.erome.com` | ✅ Active |
| Bunkr | `https://bunkr-albums.io` | ✅ Active |
| SimpCity | `https://simpcity.su` | ✅ Active |
| JPG5 | `https://jpg5.su` | ✅ Active |

---

## Supported File Types

### Videos
```
.mp4  .mkv  .webm  .mov  .avi  .flv  .wmv  .m4v
```

### Images
```
.jpg  .jpeg  .png  .gif  .bmp  .tiff
```

### Documents
```
.pdf  .doc  .docx  .xls  .xlsx  .ppt  .pptx
```

### Compressed
```
.zip  .rar  .7z  .tar  .gz
```

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| **Language** | Python 3.10+ |
| **GUI Framework** | PySide6 (Qt for Python) |
| **HTTP Client** | requests + cloudscraper |
| **HTML Parsing** | BeautifulSoup4 |
| **Image Processing** | Pillow |
| **Database** | SQLite3 (built-in) |
| **Build Target** | Windows 10/11 |

---

## Screenshots

1. Launch the application
2. Paste a supported URL into the input field
3. Select your download destination folder
4. Choose which content types to download (images, videos, compressed)
5. Click **Download** and watch the progress

> **Note**: Screenshots are available in the `resources/screenshots/` directory.

---

## Installation

### 1. Windows

#### Using Python (Recommended)

```powershell
# Clone the repository
git clone https://github.com/Emy69/CoomerDL.git
cd CoomerDL

# Create virtual environment
python -m venv .venv

# Activate virtual environment
.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py
```

#### Using uv (Faster)

```powershell
# Clone the repository
git clone https://github.com/Emy69/CoomerDL.git
cd CoomerDL

# Create virtual environment with uv
uv venv

# Activate
.venv\Scripts\Activate

# Install dependencies
uv pip install -r requirements.txt

# Run
uv python main.py
```

---

### 2. Linux (Ubuntu/Debian)

```bash
# Install system dependencies
sudo apt update
sudo apt install python3.10 python3-venv libxcb-cursor0 libxkbcommon-x11-0 libegl1 libdbus-1-3

# Clone the repository
git clone https://github.com/Emy69/CoomerDL.git
cd CoomerDL

# Create virtual environment
python3 -m venv .venv

# Activate
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py
```

---

### 3. Linux (Fedora/RHEL)

```bash
# Install system dependencies
sudo dnf install python310 python3-pip xcb-util-cursor libxkbcommon xcb-util-egl libdbus

# Clone the repository
git clone https://github.com/Emy69/CoomerDL.git
cd CoomerDL

# Create virtual environment
python3 -m venv .venv

# Activate
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py
```

---

### 4. macOS

```bash
# Install Homebrew if not installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Python and dependencies
brew install python@3.10

# Clone the repository
git clone https://github.com/Emy69/CoomerDL.git
cd CoomerDL

# Create virtual environment
python3.10 -m venv .venv

# Activate
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py
```

---

## Running the Application

### Quick Start

```bash
# Activate virtual environment
# Windows
.venv\Scripts\Activate.ps1

# Linux/macOS
source .venv/bin/activate

# Run
python main.py
```

### Using uv (Alternative)

```bash
uv python main.py
```

### Launch Script (Linux/macOS)

You can create a convenient launch script:

```bash
#!/bin/bash
cd "$(dirname "$0")"
source .venv/bin/activate
python main.py
```

Make it executable: `chmod +x run.sh`

---

## Configuration

### Download Settings

Access Settings from the menu bar: **Settings → Downloads**

| Setting | Description | Default |
|---------|-------------|---------|
| **Max Downloads** | Concurrent download threads | 5 |
| **Retries** | Number of retry attempts on failure | 3 |
| **Retry Interval** | Seconds to wait between retries | 2.0 |
| **Rate Limit** | Minimum interval between requests | 0.0 |

### File Naming Modes

Choose how downloaded files are named:

| Mode | Format | Example |
|------|--------|---------|
| **0** | `{name}_{index}` | `image_1.jpg` |
| **1** | `{post}_{index}_{hash}` | `MyPost_1_a3f2.jpg` |
| **2** | `{post} - {id}_{index}` | `MyPost - post123_1.jpg` |
| **3** | `{date} - {post}_{index}_{hash}` | `2024-01-15 - MyPost_1_a3f2.jpg` |

### Folder Structure

Configure how directories are organized:

| Option | Structure |
|--------|-----------|
| **default** | `/downloads/username/images/` |
| **post_number** | `/downloads/username/post_123/images/` |

---

## SimpCity Cookies

SimpCity may require authentication cookies for certain content. CoomerDL provides built-in cookie management:

### Adding Cookies

1. Open **Settings → Cookies**
2. Choose one of:
   - **Paste JSON** — Paste cookies directly as JSON
   - **Import File** — Load cookies from a `.json` file
3. Click **Save Cookies**

### Cookie Format

```json
{
  "session_id": "your-session-id-here",
  "cf_clearance": "your-clearance-token"
}
```

> **Security Note**: Cookies are stored locally and only used for SimpCity downloads within the application.

---

## Download Database

CoomerDL tracks all downloaded files in a local SQLite database to prevent duplicates and enable management.

### Database Location
```
resources/config/downloads.db
```

### Features

- **Automatic duplicate detection** — Skips files already in database
- **Export capability** — Export download history to CSV
- **Browse records** — View and manage entries from Settings
- **Clear history** — Option to reset database

---

## Logs

The application maintains detailed logs with domain-aware formatting:

### Example Log Output

```
bunkr: Resolving /f/ URL ...
coomer: Fetching user posts ...
erome: Processing album URL ...
system: Download settings were applied successfully.
coomer: Download complete - 25 files, 1 skipped, 0 failed
```

### Log Location
```
resources/config/logs/
```

### Exporting Logs

1. Open **Settings → Logs**
2. Click **Export Logs**
3. Choose destination and format (TXT or CSV)

---

## Language Support

### Supported Languages

- **English** (en) — Default
- **Español** (es) — Spanish

### How Translations Work

The app uses a key-based translation system. Translation files are located in:

```
resources/config/i18n/
├── languages.json  # Language registry
├── en.json         # English strings
└── es.json         # Spanish strings
```

### Translation File Structure

```json
{
  "DOWNLOAD": "Download",
  "SETTINGS": "Settings",
  "INVALID_URL": "Invalid URL",
  "DOWNLOAD_COMPLETE": "Download complete - {count} files"
}
```

### Adding a New Language in a Fork

1. Fork the repository on GitHub
2. Copy `resources/config/i18n/en.json` to your language code (e.g., `fr.json`)
3. Translate all values while keeping keys unchanged
4. Register the language in `languages.json`:

```json
{
  "official": [
    { "code": "en", "name": "English" },
    { "code": "es", "name": "Español" }
  ],
  "community": [
    { "code": "fr", "name": "Français" }
  ]
}
```

5. Test by running the app and changing language in **Settings → General**

---

## Fork Guide

CoomerDL welcomes community contributions and forks. Here's how to customize:

### 1. Fork on GitHub

Click the **Fork** button on the main repository page.

### 2. Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/CoomerDL.git
cd CoomerDL
```

### 3. Add Upstream Remote

```bash
git remote add upstream https://github.com/Emy69/CoomerDL.git
```

### 4. Keep Updated

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

### 5. Create Feature Branch

```bash
git checkout -b my-new-feature
```

### 6. Submit Pull Request

Push your changes and open a PR against the upstream repository.

---

## Troubleshooting

### Common Issues

#### Application Won't Start

**Symptoms**: Window doesn't appear, or crashes immediately

**Solutions**:
1. Ensure Python 3.10+ is installed: `python --version`
2. Verify all dependencies: `pip install -r requirements.txt`
3. Try running with verbose output: `python -v main.py`
4. Check for Qt platform issues on Linux: `export QT_QPA_PLATFORM=offscreen`

#### "INVALID_URL" Error

**Symptoms**: URL is rejected as invalid

**Solutions**:
1. Ensure URL matches supported sites exactly
2. Check for typos in the URL
3. Verify the site is accessible in your browser

#### Download Failures

**Symptoms**: Downloads start but fail partway through

**Solutions**:
1. Increase retry count in Settings
2. Check your internet connection
3. Verify the source site isn't blocking requests
4. Try reducing max concurrent downloads
5. For SimpCity: verify cookies are properly configured

#### Missing Dependencies

**Error**: `ModuleNotFoundError: No module named 'xxx'`

**Solution**:
```bash
pip install -r requirements.txt
```

#### Permission Denied

**Error**: Cannot write to download folder

**Solutions**:
1. Run terminal as Administrator (Windows)
2. Change download folder to a user-writable location
3. Check folder permissions

### Getting Help

- **Discord**: [Join our community](https://discord.gg/ku8gSPsesh)
- **GitHub Issues**: Open an issue for bugs or feature requests
- **Discussions**: Use GitHub Discussions for questions

---

## CLI Alternatives

If you prefer command-line tools, check these related projects:

- **[Coomer CLI](https://github.com/Emy69/Coomer-cli)** — Command-line interface for Coomer
- **[SimpCity CLI](https://github.com/Emy69/SimpCityCLI)** — Command-line interface for SimpCity

---

## Support

If CoomerDL helps you, consider supporting development:

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-FFDD00.svg?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/emy_69)
[![Support on Patreon](https://img.shields.io/badge/Support%20on%20Patreon-FF424D.svg?style=for-the-badge&logo=patreon&logoColor=white)](https://www.patreon.com/emy69)

---

## Community

Join the Discord server for real-time support and discussions:

[![Join Discord](https://img.shields.io/badge/Join-Discord-7289DA.svg?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/ku8gSPsesh)

---

## Downloads

Pre-built executables for Windows are available on the Releases page:

**[Download Latest Release](https://github.com/Emy69/CoomerDL/releases)**

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Thanks to all contributors and community members
- Built with [PySide6](https://www.qt.io/qt-for-python) and [requests](https://docs.python-requests.org/)
