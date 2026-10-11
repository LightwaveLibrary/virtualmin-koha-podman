# Installation

> Release candidate. Test on a fresh, disposable Virtualmin virtual server before production use.

1. Provision a Virtualmin virtual server or sub-server with working HTTPS and HTTP-to-HTTPS redirect.
2. Verify Virtualmin Podman support and rootless container prerequisites.
3. Review `recipes/koha.json`, including its secrets and persistent volume declarations.
4. Install the recipe on the Virtualmin Pro host at `/etc/webmin/virtualmin-podman/recipes/koha.json`. Create the directory if necessary:

   ```bash
   sudo mkdir -p /etc/webmin/virtualmin-podman/recipes
   sudo curl -fL https://raw.githubusercontent.com/LightwaveLibrary/virtualmin-koha-podman/main/recipes/koha.json -o /etc/webmin/virtualmin-podman/recipes/koha.json
   python3 -m json.tool /etc/webmin/virtualmin-podman/recipes/koha.json >/dev/null
   ```

   The curl command requires the GitHub repository to be public. Otherwise download [`koha.json`](../recipes/koha.json) while authenticated and transfer it to the same path. Check your installed Virtualmin version for recipe discovery or refresh requirements.
5. Deploy the Zebra variant and wait for the database, bootstrap, web, Plack, cron, Zebra, and workers to stabilize.
6. Open the Koha installer via the HTTPS site and finish configuration.
7. Verify OPAC, staff interface, catalog searching, background jobs, and container restarts.

**Security:** Never expose the Koha database password in public HTML or JavaScript. The original deployment recipe contained an installer auto-login page that did so. Do not publish or deploy that original implementation unchanged.
