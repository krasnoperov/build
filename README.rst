Private Build Infrastructure
============================

Project development environment for Continuous Deployment and Crash Monitoring.
This set of roles includes:

 * TeamCity
 * Sentry
 * PyPi Server
 * Mail server

Installation
------------

 1. Edit settings `inventory/group_vars/all/main.yml`
 2. Edit secret settings in vault: `inventory/group_vars/all/vault.yml`
 3. Provide sentry key and certificate in `playbook/roles/sentry/files/`. Encrypt key with openssl and `{{sentry_ssl_passphrase}}`
 4. Provide pypiserver key and certificate in `playbook/roles/pypiserver/files/`. Encrypt key with openssl and `{{pypiserver_ssl_passphrase}}`
 4. Run `ansible-playbook -i inventory/production playbook/site.yml --ask-vault-pass`

All services are deployed to the single server. Check `inventory/production` for details.

If basic domain is `krasnoperov.me`, then services will be available at:
 * teamcity.krasnoperov.me
 * sentry.krasnoperov.me
 * pypi.krasnoperov.me

Steps after installation
------------------------

 1. Configure DNS records (SPF/DKIM for mail and A/CNAME for each service)
 2. Configure Teamcity through it's web interface
 3. Configure Sentry through it's web interface

Feel free to contact me if you have any questions.