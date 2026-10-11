# Installation

> Release candidate. Test on a fresh, disposable Virtualmin virtual server before production use.

1. Provision a Virtualmin virtual server or sub-server with working HTTPS and HTTP-to-HTTPS redirect.
2. Verify Virtualmin Podman support and rootless container prerequisites.
3. Review `recipes/koha.json`, including its secrets and persistent volume declarations.
4. Install the recipe in Virtualmin's Podman recipe directory, following your installed Virtualmin version's recipe management instructions.
5. Deploy the Zebra variant and wait for the database, bootstrap, web, Plack, cron, Zebra, and workers to stabilize.
6. Open the Koha installer via the HTTPS site and finish configuration.
7. Verify OPAC, staff interface, catalog searching, background jobs, and container restarts.

**Security:** Never expose the Koha database password in public HTML or JavaScript. The original deployment recipe contained an installer auto-login page that did so. Do not publish or deploy that original implementation unchanged.
