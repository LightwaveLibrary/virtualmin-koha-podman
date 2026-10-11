# Configuration

The supplied recipe uses MariaDB 11.4, Memcached 1.6, and `koha/koha:stable` with Zebra indexing. It runs as rootless Podman containers and persists the Koha instance, site configuration, Apache configuration, logs, cache, and database through declared volumes.

The recipe declares a `db_password` deployment secret and targets amd64 and arm64 architectures. It sets an application port of 8080, with the Koha staff interface routed under `/cgi-bin/koha/mainpage.pl` on the same public site.

Before reusing it, verify image compatibility, startup ordering, host sizing, domain proxying, volume ownership, and the installer security changes. No fresh-deployment validation has been recorded for this release candidate.
