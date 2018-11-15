GitLab Runner 
=============

This role will allow you to install SSL certificates through [Let's Encrypt](https://letsencrypt.org/).

Requirements
------------

This role requires Ansible 2.5 or higher.

Role Variables
--------------

### Package options:
  
`lets_encrypt_hostname`
Host for which to install new certificate.

`lets_encrypt_agreement`
URI to a terms of service document you agree to when using the ACME v1 service at `lets_encrypt_endpoint`.

`lets_encrypt_endpoint`
This is the entry point URL to access CA server API. (default: https://acme-v01.api.letsencrypt.org/directory)

`lets_encrypt_directories_certs`
Directory where certificates will be stored. (default: /tmp)

`lets_encrypt_directories_data`
Directory for making challenge data. (default: /tmp/data)
Note! This directory must be available on your server(nginx|Apache|etc).

Add role to project:
----------------
Add role into your requirements(_requirements.yml_ for example):
```yaml
- src: https://github.com/lexa-uw/ansible-role-letsencrypt
  version: v1.1.0
  name: letsencrypt
```

Install role: `ansible-galaxy install -r ./requirements.yml --roles-path ./roles/`

Playbook example:
----------------
```yaml
- hosts: all
  vars_files:
    - vars/main.yml
  roles:
    - { role: letsencrypt }
```

Inside `vars/main.yml`
```yaml
lets_encrypt_hostname: host.name
lets_encrypt_directories_certs: "/etc/nginx/ssl"
lets_encrypt_directories_data: "/var/www/data"
```
