# Mycelium Guide

Mycelium Guide is the public documentation and tutorial website for setting up and using the Mycelium encrypted overlay network.

## What this is

Mycelium Guide provides step-by-step instructions for installing, configuring, and troubleshooting Mycelium on various platforms. It serves as the primary learning resource for new Mycelium users and as a reference for ongoing operation.

The documentation covers:
- Installation on Linux, macOS, Windows, iOS, and Android
- Quick start guides for connecting to the network
- Configuration options and CLI reference
- Daily usage patterns including SOCKS5 proxy setup
- Troubleshooting common issues

## What this repository contains

- `docs/` — Jekyll-based documentation source files
  - `installation.md` — Platform-specific installation instructions
  - `quick-start.md` — Getting connected in under 5 minutes
  - `configuration.md` — Config files and CLI options
  - `usage.md` — Daily usage patterns and examples
  - `troubleshooting.md` — Common issues and solutions
- `SETUP.md` — Guide for setting up GitHub Pages deployment
- `.github/workflows/` — GitHub Actions workflow for automated deployment

## Mycelium

Mycelium is the network layer used to provide secure, peer-to-peer connectivity between nodes, services, and users. It enables decentralized networking across the infrastructure stack and is used as part of the ThreeFold Grid deployment.

## Role in the stack

Mycelium Guide sits alongside the Mycelium network implementation as its user-facing documentation. It explains how to install and operate Mycelium clients, configure peers, and use network features such as the SOCKS5 proxy. The guide is published via GitHub Pages and is kept in sync with Mycelium releases.

## Relation to ThreeFold

This technology is used within the ThreeFold ecosystem and was first deployed on the ThreeFold Grid. The component itself is designed as reusable infrastructure technology and should be understood by its technical function first, independent of any specific deployment.

## Ownership

This repository is owned and maintained by TF-Tech NV, a Belgian company responsible for the development and maintenance of this technology.

## Local Development

To preview the documentation locally:

```bash
cd docs
bundle install
bundle exec jekyll serve
```

Visit `http://localhost:4000/mycelium_guide/`

## Contributing

Contributions are welcome. To improve the documentation:

1. Fork this repository
2. Make your changes in the `/docs` directory
3. Test locally with Jekyll
4. Submit a pull request

## License

This project is licensed under the Apache License 2.0 — see the [LICENSE](LICENSE) file for details.
