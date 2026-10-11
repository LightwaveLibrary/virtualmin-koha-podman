# Virtualmin Koha Podman

**Lightwave Library** — Koha deployment recipe for Virtualmin with rootless Podman.

> **Release candidate — verify on a fresh test server before production use.**

## Overview

The original working recipe deploys Koha with MariaDB 11.4, Memcached 1.6, Zebra indexing, Plack, web, cron, and background workers. It targets amd64 and arm64 and uses persistent volumes for catalog data and configuration.

## Current status

- An existing deployment was stabilized by allowing the `koha-koha` service user to traverse `/etc/koha/sites` (`chmod 755` on the directory; do not relax permissions on the configuration file).
- The original recipe generates a browser-accessible installer auto-login page that includes a database password. **Do not publish or deploy that mechanism unchanged.**
- A revised recipe is available at [`recipes/koha.json`](recipes/koha.json); it still requires fresh-install validation.

## Install the recipe

Download [`recipes/koha.json`](recipes/koha.json) and place it on the Virtualmin Pro host at:

```text
/etc/webmin/virtualmin-podman/recipes/koha.json
```

Run as root (or with sudo):

```bash
sudo mkdir -p /etc/webmin/virtualmin-podman/recipes
sudo curl -fL https://raw.githubusercontent.com/LightwaveLibrary/virtualmin-koha-podman/main/recipes/koha.json -o /etc/webmin/virtualmin-podman/recipes/koha.json
python3 -m json.tool /etc/webmin/virtualmin-podman/recipes/koha.json >/dev/null
```

**Note:** The download command works once the repository is public; for a private repository, download the JSON file while signed in and copy it to that path. See [installation details](docs/installation.md).

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
