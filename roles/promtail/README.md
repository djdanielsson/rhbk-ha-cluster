promtail
========

The role is used to setup and configure Promtail.

<!--start argument_specs-->
Role Defaults
-------------

* No defaults

Role Variables
--------------

| Variable             | Description                          | Default                                                               |
|:---------------------|:-------------------------------------|:----------------------------------------------------------------------|
| `promtail_directory` | promtail directory path              | `/opt/promtail`                                                       |
| `promtail_loki_url`  | promtail loki URL                    | `http://grafana.internal.ansiblemiddleware.com:3100/loki/api/v1/push` |
| `promtail_job_name`  | promtail job name                    | `default`                                                             |
| `promtail_logfile`   | promtail logfile path                | `/var/log/messages`                                                   |
| `promtail_region`    | promtail configured for which region | `us-east-1`                                                           |
| `promtail_host`      | promtail hostnames                   | `"{{ inventory_hostname }}"`                                          |
| `promtail_version`   | promtail versions                    | `2.5.0`                                                               |

<!--end argument_specs-->

Dependencies
------------

* community.general

Example Playbook
----------------

License
-------

[Apache License Version 2.0](https://github.com/ansible-middleware/rhbk-ha-cluster/blob/main/LICENSE)

Author Information
------------------

* [Guido Grazioli](https://github.com/guidograzioli)
* [Harsha Cherukuri](https://github.com/hcherukuri)
* [Ranabir Chakraborty](https://github.com/RanabirChakraborty)
