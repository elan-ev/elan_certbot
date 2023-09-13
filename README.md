Ansible: Elan Certbot Role
==============================

This Ansible role configures TLS certificate renewal via certbot.
This role is exactly the same as https://github.com/elan-ev/opencast_certbot,
without the [opencast_nginx](https://github.com/elan-ev/opencast_nginx) dependency (see https://github.com/elan-ev/opencast_certbot/pull/3).
This role will work with both the [opencast_nginx](https://github.com/elan-ev/opencast_nginx)
and the [simple_nginx_reverse_proxy](https://github.com/elan-ev/simple_nginx_reverse_proxy),
but likely not with a standard nginx or anything else.

Role Variables
--------------

- `elan_certbot_letsencrypt_email`: The email address for Let's Encrypt account (_required_). This is used by Let's Encrypt to send certificate expiration warnings if necessary.
- `elan_certbot_domains`: A list specifying the domains for which the certificate should be valid. Defaults to `["{{ inventory_hostname }}"]`.
- `elan_certbot_expand_existing`: A boolean flag that you can use e.g. as extra variable when running a playbook, to force certbot to expand already existing certificates. You should not set this to `true` as default, but only when you actually need it.
- `elan_certbot_ca`: You can specify if you want to use `letsencrypt` (the default) or use `sectigo` with eab for DFN ACME. You then also need to define `elan_certbot_eab_kid` and `elan_certbot_eab_hmac`.

Example Playbook
----------------

Example of how to configure and use the role:

```yaml
- hosts: servers
  become: true
  roles:
    - role: elan.elan_certbot
      elan_certbot_letsencrypt_email: admin@example.com
```
