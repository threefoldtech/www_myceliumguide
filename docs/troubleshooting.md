---
layout: default
title: Troubleshooting
---

# Troubleshooting

Common problems and solutions when using Mycelium.

## Installation Issues

### "Command not found" after installation

**Problem:** Mycelium binary not in PATH.

**Solutions:**
```bash
# Check where you installed it
find /usr/local/bin -name "*mycelium*" 2>/dev/null

# Add to PATH (add to ~/.bashrc or ~/.profile)
export PATH="$PATH:/usr/local/bin"

# Or run directly with full path
/usr/local/bin/mycelium --version
```

### Permission denied on macOS/Linux

**Problem:** Need sudo for TUN interface.

**Solution:**
```bash
sudo mycelium --peers tcp://188.40.132.242:9651
```

## Connection Issues

### Cannot connect to peers

**Problem:** Network/firewall blocking connections.

**Solutions:**
```bash
# Test basic connectivity
ping -c 3 188.40.132.242

# Check if ports are open
telnet 188.40.132.242 9651

# Try different peers
mycelium --peers tcp://185.69.166.7:9651 quic://65.21.231.58:9651
```

### No IPv6 connectivity

**Problem:** IPv6 not available or disabled.

**Solutions:**
```bash
# Check IPv6 status
ip -6 addr show

# Enable IPv6 (Linux)
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=0

# Test IPv6 connectivity
ping6 -c 3 google.com
```

### TUN interface not created

**Problem:** Permission issues or TUN module not loaded.

**Solutions:**
```bash
# Linux - load TUN module
sudo modprobe tun

# Check TUN device exists
ls -la /dev/net/tun

# Try different interface name
mycelium --tun-name myc0 --peers tcp://188.40.132.242:9651
```

## API Issues

### "Connection refused" on localhost:8989

**Problem:** API not enabled or wrong port.

**Solutions:**
```bash
# Enable API explicitly
mycelium --api-addr 127.0.0.1:8989 --peers tcp://188.40.132.242:9651

# Check if process is running
ps aux | grep mycelium

# Try different port
mycelium --api-addr 127.0.0.1:9999 --peers tcp://188.40.132.242:9651
```

### JSON-RPC errors

**Problem:** Malformed requests or method not found.

**Solutions:**
```bash
# Test with simple curl
curl http://localhost:8989/peers

# Check API documentation
curl http://localhost:8989/rpc -X POST \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"help","id":1}'
```


## SOCKS5 Proxy Issues

### "No valid proxy available"

**Problem:** No peers with SOCKS5 service found.

**Solutions:**
```bash
# Start proxy discovery
curl -X POST http://localhost:8989/rpc \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"startProxyProbe","id":1}'

# Wait and check again
sleep 60
curl http://localhost:8989/proxies

# Try specific remote proxy
curl -X POST http://localhost:8989/rpc \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"connectProxy","params":["[peer-address]:1080"],"id":1}'
```

### Applications can't connect to proxy

**Problem:** Proxy not bound or firewall blocking.

**Solutions:**
```bash
# Check if proxy is active
netstat -tlnp | grep 1080

# Test proxy manually
curl --socks5-hostname 127.0.0.1:1080 https://httpbin.org/ip

# Check firewall
sudo ufw status  # Linux
# Or check Windows firewall settings
```

## Performance Issues

### Slow connections

**Problem:** Poor peer selection or network issues.

**Solutions:**
```bash
# Try more peers
mycelium --peers \
  tcp://188.40.132.242:9651 \
  tcp://185.69.166.7:9651 \
  tcp://65.21.231.58:9651

# Check connection quality
ping6 [peer-address]

# Monitor routing table
curl http://localhost:8989/routes
```

### High CPU usage

**Problem:** Too many peers or debug mode enabled.

**Solutions:**
```bash
# Reduce number of peers
mycelium --peers tcp://188.40.132.242:9651

# Check for debug logging
# Remove any --debug or --verbose flags

# Monitor resource usage
top -p $(pgrep mycelium)
```

## Mobile Platform Issues

### iOS Installation Issues

**Problem:** App installation or TUN interface problems.

**Solutions:**
- iOS requires developer certificates for installation
- TUN interface may need to be enabled in Settings > VPN & Network
- Check that the mobile app is built with proper iOS configuration
- Some iOS versions may have limitations on TUN interface usage

### Android Installation Issues

**Problem:** APK installation or TUN interface permissions.

**Solutions:**
- Enable "Unknown sources" in Android settings for sideloading
- Grant TUN interface permissions in Android VPN settings
- Ensure Android 7.0+ with TUN interface support
- Check that the APK is built for your Android architecture (ARM/ARM64/x86)

### Mobile Network Performance

**Problem:** Battery drain or slow performance on mobile devices.

**Solutions:**
- Mobile versions may use more battery due to overlay networking
- Consider using private networks for mobile-to-mobile communication
- Reduce number of peers on mobile devices to save battery
- Monitor network usage in device settings

## Configuration Issues

### Config file not loaded

**Problem:** Wrong path or syntax error.

**Solutions:**
```bash
# Test config syntax
mycelium --config-file /path/to/config.toml --help

# Use absolute paths
mycelium --config-file $HOME/.config/mycelium.toml

# Check file permissions
ls -la ~/.config/mycelium.toml
```

## Getting More Help

1. **Check logs:** Look for error messages in console output
2. **Test connectivity:** Use `ping6` and `telnet` to test basic networking
3. **Simplify:** Try with minimal configuration first
4. **Update:** Make sure you're using the latest version
5. **Community:** Check GitHub issues for similar problems

If problems persist, visit the [Mycelium project repository](https://github.com/threefoldtech/mycelium) for advanced troubleshooting.

---

*Still having issues? Visit the [project repository](https://github.com/threefoldtech/mycelium) for more detailed troubleshooting information.*
