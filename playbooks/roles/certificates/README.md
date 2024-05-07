certificates
========

The role is used to install required certificates and keystore.

<!--start argument_specs-->
Role Defaults
-------------

* No defaults

Role Variables
--------------

| Variable                             | Description                                         | Default            |
|:-------------------------------------|:----------------------------------------------------|:-------------------|
| `certificates_install_keystore`      | Certificates inatll keystore boolean value          | `False`            |
| `certificates_install_trust_ca`      | Certificates inatll keystore CA certs boolean value | `True`             |
| `certificates_ca_cn`                 | CA certificate for which url                        | `rhssocrossdc.com` |
| `certificates_trust_ca_password`     | Certificate CA password                             | `changeit`         |
| `certificates_tls_certs_lookup_path` | Certificates TLS certs lookup path                  | ` `                |

<!--end argument_specs-->

Dependencies
------------

* amazon.aws
* community.aws
* community.general

Example Playbook
----------------

License
-------

[Apache License Version 2.0](https://github.com/ansible-middleware/rhbk-datagrid-aws/blob/main/LICENSE)

Author Information
------------------

* [Guido Grazioli](https://github.com/guidograzioli)
* [Harsha Cherukuri](https://github.com/hcherukuri)
* [Ranabir Chakraborty](https://github.com/RanabirChakraborty)
