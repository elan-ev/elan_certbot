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

- `elan_certbot_letsencrypt_email`
   - Email address for Let's Encrypt account (_required_)
	- This is used by Let's Encrypt to send certificate expiration warnings if necessary.


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
