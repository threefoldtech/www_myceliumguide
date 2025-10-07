---
layout: default
title: Configuration
---

# Configuration

Customize Mycelium for your specific needs using configuration files or command-line options.

## Basic Configuration File

Create a file called `mycelium.toml` in your home directory:

```toml
# Basic configuration
peers = [
  "tcp://188.40.132.242:9651",
  "quic://185.69.166.8:9651"
]

# Network interface (optional)
tun_name = "mycelium"

# API port for management (optional)
api_addr = "127.0.0.1:8989"

# Disable TUN interface if only using message system (optional)
no_tun = false
```

## Command-Line Options

You can also configure Mycelium using command-line flags:

```bash
# Basic connection with custom port
mycelium --peers tcp://188.40.132.242:9651 --tcp-listen-port 9651

# Use different TUN interface name
mycelium --peers tcp://188.40.132.242:9651 --tun-name utun9

# Enable API on different port
mycelium --peers tcp://188.40.132.242:9651 --api-addr 127.0.0.1:9999
```

## Private Networks

For private networks, you need the private binary and shared secrets:

1. **Use the private binary:**
   ```bash
   # Linux/macOS
   wget https://github.com/threefoldtech/mycelium/releases/latest/download/mycelium-private-linux-x64.tar.gz

   # Windows
   # Download mycelium-private_installer.msi from releases
   ```

2. **Create network key file:**
   ```bash
   # Generate a 32-byte random key
   openssl rand -hex 32 > network.key
   ```

3. **Configure private network:**
   ```toml
   # Private network configuration
   network_name = "my-private-network"
   network_key_file = "network.key"
   ```

4. **Start private node:**
   ```bash
   mycelium-private --network-name "my-private-network" --network-key-file network.key
   ```

## Configuration Locations

Mycelium looks for configuration files in these locations:

- **Linux:** `$HOME/.config/mycelium.toml`
- **macOS:** `$HOME/Library/Application Support/ThreeFold Tech/Mycelium/mycelium.toml`
- **Windows:** `%APPDATA%\ThreeFold Tech\Mycelium\mycelium.toml`

Command-line options override configuration file settings.

## Common Configuration Examples

### High Security Setup
```toml
peers = [
  "tcp://188.40.132.242:9651",
  "quic://185.69.166.8:9651"
]
tcp_listen_port = 9651
api_addr = "127.0.0.1:8989"  # Only localhost access
no_tun = false
```

### Message-Only Setup (No Network Interface)
```toml
peers = [
  "tcp://188.40.132.242:9651"
]
no_tun = true  # Only message system, no IP networking
api_addr = "127.0.0.1:8989"
```

### Development Setup
```toml
peers = [
  "tcp://188.40.132.242:9651"
]
tcp_listen_port = 9651
api_addr = "127.0.0.1:8989"
# Debug logging (if available)
# log_level = "debug"
```

## Next Steps

- **[Start using Mycelium](usage)** - Learn daily usage patterns
- **[Troubleshoot issues](troubleshooting)** - If configuration isn't working

---

*Configuration set? Now learn how to [use Mycelium daily](usage).*
