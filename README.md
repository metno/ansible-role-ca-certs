ca-certs
========

Role for adding one or more extra CA certificates to the machine store.

Version
-------

* `2.1.0` --- added ubuntu noble 24.04 support
* `2.0.1` --- bug fix, ansible-lint
* `2.0.0` --- upgraded to ansible 2.12
* `1.4.0` --- added RHEL9 and CentOS 8 Stream support
* `1.3.0` --- added  Ubuntu Jammy 22.04 support, removed CentOS 8 support
* `1.2.0` --- added RHEL 8 support, removed CentOS 6, trusty, precise
* `1.1.1` --- workaround for false positive lint error
* `1.1.0` --- added ubuntu focal, 20.04
* `1.0.1` --- tested with Ansible 2.9.11
* `1.0.0` --- initial role
* `master` --- latest development version

Requirements
------------

This role is limited to

* Ubuntu 24.04 - Noble
* Ubuntu 22.04 - Jammy
* Ubuntu 20.04 - Focal
* Ubuntu 18.04 - Bionic
* Ubuntu 16.04 - Xenial
* CentOS 7
* CentOS 8 Stream
* RHEL 8
* RHEL 9

Role Variables
--------------

* `ca_certs` --- list os certificates to add to the store, default `[]`.

Dependencies
------------

None.

Example Playbook
----------------

Test with disting out a self-signed certificate generated with

```bash
openssl req -x509 -subj CN=machine.foo.bar -addext subjectAltName=DNS:foo.bar -newkey rsa:4096 -keyout machine.key -nodes -out machine-fullchain.pem -days 365
```

    - hosts: servers
      roles:
         - role: ca-certs
           ca_certs:
             - |
               -----BEGIN CERTIFICATE-----
               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
               xS/TZoJ6ozZiLMTbwQ741QUzjaqTKOqAfNHtwOU=
               -----END CERTIFICATE-----


Testing
-------

### Test environment for all OSes

```bash
cd tests
vagrant up
```

### Rerun role

Run role on all OSes again.

```bash
vagrant provision
```

### Debug interactively

This uses cluster ssh to work with all vagrant boxes at the same time.

```bash
vagrant ssh-config > ~/.ssh/config
cat ~/.ssh/config | grep ^Host | cut -d\  -f2 | xargs cssh
```

License
-------

GPLv2

Author Information
------------------

Created 2020 by [Arnulf Heimsbakk](mailto:arnulf.heimsbakk@met.no) for MET Norway.

###### set vim: spell spelllang=en:
