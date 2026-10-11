# Troubleshooting

## Zebra or workers restart continuously

Check whether the service account can traverse `/etc/koha/sites` and read `/etc/koha/sites/koha/koha-conf.xml`.

A confirmed failure was `/etc/koha/sites` with permissions `0750 root:root`, preventing the `koha-koha` user from accessing its configuration.

On the affected Koha web container, the corrective command was:

```sh
chmod 755 /etc/koha/sites
```

Do **not** make `koha-conf.xml` world-readable: it may contain credentials. The recipe's boot component should establish directory traversal permissions both before and after initial bootstrap. Recheck actual ownership and modes before applying a fix to a different installation.

## High CPU

Inspect per-container restart counts and logs first. Repeated failed service starts can cause excessive CPU usage. A production deployment saw CPU usage drop substantially after correcting the directory permissions.
