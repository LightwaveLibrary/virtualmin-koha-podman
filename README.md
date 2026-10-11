# Virtualmin Koha Podman

**Lightwave Library** — Koha deployment recipe for Virtualmin with rootless Podman.

> **Private release candidate — not yet verified for a clean installation or approved for public distribution.**

## Overview

The original working recipe deploys Koha with MariaDB 11.4, Memcached 1.6, Zebra indexing, Plack, web, cron, and background workers. It targets amd64 and arm64 and uses persistent volumes for catalog data and configuration.

## Current status

- An existing deployment was stabilized by allowing the `koha-koha` service user to traverse `/etc/koha/sites` (`chmod 755` on the directory; do not relax permissions on the configuration file).
- The original recipe generates a browser-accessible installer auto-login page that includes a database password. **Do not publish or deploy that mechanism unchanged.**
- A community-safe revised recipe still requires verification on a disposable fresh installation before being added here.

## Video walkthrough

[Watch the deployment walkthrough on YouTube](https://youtu.be/7Y9o2s2cDEM).

## Documentation

- [Installation](docs/installation.md)
- [Configuration](docs/configuration.md)
- [Troubleshooting](docs/troubleshooting.md)
- [Security](docs/security.md)
- [Upgrading](docs/upgrading.md)

## License

MIT; see [LICENSE](LICENSE).

## Acknowledgment

Made possible by [Lightwave Library](https://lightwavelibrary.com/).
