# Development Infrastructure

Project development environment for continuous deployment and crash monitoring

 * TeamCity
 * Sentry
 * PyPi Server
 * Certificate Authority
 * Mail server

## Installation

1. Edit `inventory/group_vars/all/main.yml`
2. Provide secret passwords in `inventory/group_vars/all/vault.yml`
3. Provide sentry key and certificate in `playbook/roles/sentry/sentry.key`
4. Run `ansible-playbook -i inventory/production playbook/site.yml`

All services are deployed to the single server. Check `inventory/production` for details.

In case basic domain is `krasnoperov.me`, services will be available at:
 * teamcity.krasnoperov.me
 * sentry.krasnoperov.me
 * pypi.krasnoperov.me

## Steps after installation

1. Configure DNS records (SPF/DKIM for email and A/CNAME for each service)
2. Configure Teamcity through it's web interface
3. Configure Sentry through it's web interface

Feel free to contact me if you have any questions.