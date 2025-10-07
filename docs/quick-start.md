---
layout: default
title: Quick Start
---

# Quick Start

Get your Mycelium node connected to the global network in under 5 minutes.

## Public Peers

Here are all the available public peers you can connect to:

| ID | Region | IPv4 | IPv6 | TCP Port | QUIC Port | Mycelium IP |
|----|--------|------|------|----------|-----------|-------------|
| 01 | DE | 188.40.132.242 | 2a01:4f8:221:1e0b::2 | 9651 | 9651 | 54b:83ab:6cb5:7b38:44ae:cd14:53f3:a907 |
| 02 | DE | 136.243.47.186 | 2a01:4f8:212:fa6::2 | 9651 | 9651 | 40a:152c:b85b:9646:5b71:d03a:eb27:2462 |
| 03 | BE | 185.69.166.7 | 2a02:1802:5e:0:ec4:7aff:fe51:e80d | 9651 | 9651 | 597:a4ef:806:b09:6650:cbbf:1b68:cc94 |
| 04 | BE | 185.69.166.8 | 2a02:1802:5e:0:ec4:7aff:fe51:e36b | 9651 | 9651 | 549:8bce:fa45:e001:cbf8:f2e2:2da6:a67c |
| 05 | FI | 65.21.231.58 | 2a01:4f9:6a:1dc5::2 | 9651 | 9651 | 410:2778:53bf:6f41:af28:1b60:d7c0:707a |
| 06 | FI | 65.109.18.113 | 2a01:4f9:5a:1042::2 | 9651 | 9651 | 488:74ac:8a31:277b:9683:c8e:e14f:79a7 |
| 07 | US-EAST | 209.159.146.190 | 2604:a00:50:17b:9e6b:ff:fe1f:e054 | 9651 | 9651 | 4ab:a385:5a4e:ef8f:92e0:1605:7cb6:24b2 |
| 08 | US-WEST | 5.78.122.16 | 2a01:4ff:1f0:8859::1 | 9651 | 9651 | 4de:b695:3859:8234:d04c:5de6:8097:c27c |
| 09 | SG | 5.223.43.251 | 2a01:4ff:2f0:3621::1 | 9651 | 9651 | 5eb:c711:f9ab:eb24:ff26:e392:a115:1c0e |
| 10 | IND | 142.93.217.194 | 2400:6180:100:d0::841:2001 | 9651 | 9651 | 445:465:fe81:1e2b:5420:a029:6b0:9f61 |

## 1. Start with Public Nodes

Connect to the public Mycelium network using these stable nodes:

```bash
mycelium --peers tcp://188.40.132.242:9651 quic://185.69.166.8:9651
```

On Windows, run this in Command Prompt:
```cmd
mycelium --peers tcp://188.40.132.242:9651 quic://185.69.166.8:9651
```

## 2. Check Your Node Info

In a new terminal, check your node's details:

```bash
mycelium inspect --json
```

You should see something like:
```json
{
  "publicKey": "abd16194646defe7ad2318a0f0a69eb2e3fe939c3b0b51cf0bb88bb8028ecd1d",
  "address": "5c4:c176:bf44:b2ab:5e7e:f6a:b7e2:11ca"
}
```

**Save your IPv6 address** (the "address" field) - this is how other nodes will reach you.

## 3. Test Connectivity

Ping another node in the network:

```bash
ping6 54b:83ab:6cb5:7b38:44ae:cd14:53f3:a907
```

If you get responses, you're connected! Your node is now part of the global Mycelium network.

## 4. Keep It Running

Mycelium needs to keep running to maintain connections. In a production environment:

- **Linux/macOS:** Use systemd, launchd, or run in background with `nohup`
- **Windows:** Use Task Scheduler or run in Command Prompt

Example background run:
```bash
nohup mycelium --peers tcp://188.40.132.242:9651 quic://185.69.166.8:9651 &
```

## What's Next?

- **[Customize your setup](configuration)** - Change ports, add more peers
- **[Start using the network](usage)** - Set up proxy and use the network
- **[Troubleshoot issues](troubleshooting)** - If something isn't working

## Multiple Peers (Better Connectivity)

For better reliability, connect to multiple public nodes:

```bash
mycelium --peers \
  tcp://188.40.132.242:9651 \
  quic://185.69.166.8:9651 \
  tcp://185.69.166.7:9651 \
  quic://65.21.231.58:9651
```

---

*Connected successfully? Great! Now learn how to [configure](configuration) and [use](usage) Mycelium.*
