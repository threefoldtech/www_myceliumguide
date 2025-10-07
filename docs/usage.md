---
layout: default
title: Usage
---

# Usage Guide

Learn how to use Mycelium for daily tasks like setting up application proxies and network connectivity.

## Check Node Status

Monitor your Mycelium node:

```bash
# View node information
mycelium inspect

# View in JSON format
mycelium inspect --json

# Check connected peers
curl http://localhost:8989/peers
```

## SOCKS5 Proxy

Route application traffic through Mycelium network.

### 1. Discover Proxies

```bash
# Start proxy discovery
curl -X POST http://localhost:8989/rpc \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "startProxyProbe",
    "params": [],
    "id": 1
  }'

# Check discovered proxies
curl http://localhost:8989/proxies
```

### 2. Connect to Proxy

```bash
# Connect to best available proxy
curl -X POST http://localhost:8989/rpc \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "connectProxy",
    "params": [""],
    "id": 1
  }'

# Or connect to specific node
curl -X POST http://localhost:8989/rpc \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "connectProxy",
    "params": ["[destination-ipv6]:1080"],
    "id": 1
  }'
```

### 3. Use the Proxy

Configure applications to use `127.0.0.1:1080` as SOCKS5 proxy:

- **Web browsers:** Set proxy to `127.0.0.1:1080`
- **Command line:** `export http_proxy=socks5://127.0.0.1:1080`
- **curl:** `curl --socks5-hostname 127.0.0.1:1080 https://example.com`

### 4. Disconnect Proxy

```bash
curl -X POST http://localhost:8989/rpc \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "disconnectProxy",
    "params": [],
    "id": 1
  }'
```

## Daily Usage Patterns

### Start Mycelium
```bash
# Start with default config
mycelium

# Or with specific config file
mycelium --config-file ~/.config/mycelium.toml

# Run in background
nohup mycelium --peers tcp://188.40.132.242:9651 &
```

### Stop Mycelium
```bash
# Find process ID
ps aux | grep mycelium

# Kill the process
kill [process-id]
```

### Monitor Connections
```bash
# Check API status
curl http://localhost:8989/peers

# View routing table
curl http://localhost:8989/routes

# Check network statistics
curl http://localhost:8989/metrics
```

## Real-World Examples

### Remote Access
Set up SOCKS5 proxy to access home network from anywhere:

1. Run Mycelium on home computer
2. Connect to proxy from remote device
3. Access `192.168.1.100:8080` through proxy

### IoT Device Networking
Connect IoT devices through Mycelium overlay:

1. Install Mycelium on each device
2. Configure with same peers or private network
3. Devices can communicate securely regardless of physical location

### Backup Connectivity
Use Mycelium as backup when main internet fails:

```bash
# Route specific traffic through Mycelium
iptables -t mangle -A OUTPUT -d [important-ip] -j MARK --set-mark 30
```

## Next Steps

- **[Troubleshoot problems](troubleshooting)** - When things don't work
- **[Learn more](https://github.com/threefoldtech/mycelium)** - Technical documentation for advanced usage

---

*Using Mycelium effectively? Check [troubleshooting](troubleshooting) for common issues.*
