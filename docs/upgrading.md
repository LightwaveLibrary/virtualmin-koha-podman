# Upgrading

The recipe uses floating `koha/koha:stable` tags for Koha services. Pulling that tag later can install a different Koha release and may require database migrations.

1. Back up and verify restore of the database and persistent volumes.
2. Record the currently deployed image digests and Koha version.
3. Test the target version and migration against a restored copy.
4. Upgrade the Koha application/service containers together under a planned maintenance window.
5. Do not delete or recreate database volumes as part of an application upgrade.
6. Verify catalog, staff client, OPAC, indexing, cron, and background jobs afterward.

Do not treat `stable` as a pinned or reproducible version.
