---
layout: default
title: Installation
---

# Installation Guide

Get Mycelium running on your system in a few simple steps.

## Desktop Platforms

### Linux

#### Using Pre-built Binaries

1. **Download the latest release:**
   ```bash
   wget https://github.com/threefoldtech/mycelium/releases/latest/download/mycelium-linux-x64.tar.gz
   ```

2. **Extract and install:**
   ```bash
   tar -xzf mycelium-linux-x64.tar.gz
   chmod +x mycelium
   sudo mv mycelium /usr/local/bin/
   ```

3. **Verify installation:**
   ```bash
   mycelium --version
   ```

#### Building from Source

```bash
git clone https://github.com/threefoldtech/mycelium.git
cd mycelium/myceliumd
cargo build --release
sudo mv target/release/myceliumd /usr/local/bin/mycelium
```

### macOS

#### Using Pre-built Binaries

1. **Download the latest release:**
   ```bash
   wget https://github.com/threefoldtech/mycelium/releases/latest/download/mycelium-macos-x64.tar.gz
   ```

2. **Extract and install:**
   ```bash
   tar -xzf mycelium-macos-x64.tar.gz
   chmod +x mycelium
   sudo mv mycelium /usr/local/bin/
   ```

3. **Verify installation:**
   ```bash
   mycelium --version
   ```

#### Using Homebrew (if available)

```bash
brew install threefoldtech/mycelium/mycelium
```

### Windows

1. **Download the installer:**
   Go to [releases page](https://github.com/threefoldtech/mycelium/releases) and download `mycelium_installer.msi`

2. **Run the installer:**
   Double-click the downloaded `.msi` file and follow the installation wizard.

3. **Verify installation:**
   Open Command Prompt and run:
   ```cmd
   mycelium --version
   ```

## Mobile Platforms

### iOS

Mycelium runs as a mobile app on iOS devices. Due to iOS restrictions, it operates in TUN-only mode for overlay networking.

**Installation:**
- The mobile app is available through the project's mobile directory
- Build and install using the provided iOS configuration
- Requires developer tools and certificates for installation

**Note:** iOS version focuses on network overlay functionality and may have limitations compared to desktop versions.

### Android

Mycelium runs on Android devices with full TUN interface support for overlay networking.

**Installation:**
- The mobile app is available through the project's mobile directory
- Can be built as an APK for sideloading or distributed through app stores
- Requires Android 7.0+ with TUN interface support

**Note:** Android version provides full desktop-equivalent functionality including SOCKS5 proxy support.

## Verify Installation

After installation, check that Mycelium is working:

```bash
mycelium inspect --json
```

You should see output like:
```json
{
  "publicKey": "abd16194646defe7ad2318a0f0a69eb2e3fe939c3b0b51cf0bb88bb8028ecd1d",
  "address": "5c4:c176:bf44:b2ab:5e7e:f6a:b7e2:11ca"
}
```

This shows your node's unique IPv6 address in the Mycelium network.

## Next Steps

- **[Connect to the network](quick-start)** - Get your node online
- **[Configure settings](configuration)** - Customize for your needs
- **[Start using](usage)** - Set up proxy and use the network

---

*Need help? Check [Troubleshooting](troubleshooting) for common installation issues.*
