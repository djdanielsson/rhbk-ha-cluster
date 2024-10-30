# rhbk-ha-cluster

[![CI](https://github.com/ansible-middleware/rhbk-ha-cluster/actions/workflows/ci.yml/badge.svg)](https://github.com/ansible-middleware/rhbk-ha-cluster/actions/workflows/ci.yml)

Provision and deploy a Red Hat Build of Keycloak authentication service on multi-region clusters via Ansible

### Use case of rhbk-ha-cluster collection

The primary use case of the `rhbk-ha-cluster` collection is to install Red Hat Build of Keycloak (RHBK) with high availability (HA) across multi-region clusters. This ensures that the authentication service is resilient, fault-tolerant, and capable of serving users even in the event of a regional failure. The collection automates the setup of RHBK in a highly available architecture, integrating with Data Grid for distributed caching and ensuring smooth, secure authentication.

### 0. prerequisites

* Setup multi-region clusters infrastructure.
* A database service that can be accessed from the deployment regions.
* TLS certificates for the desired domain name to provide the authentication service

### 1. create ansible.cfg

```
[defaults]
remote_user=<ssh_user>
private_key_file=<path_to_private_key>
host_key_checking=False
gathering=smart
pipelining=True

[galaxy]
server_list=galaxy,automation_hub

[galaxy_server.galaxy]
url=https://galaxy.ansible.com/

[galaxy_server.automation_hub]
url=https://cloud.redhat.com/api/automation-hub/
auth_url=https://sso.redhat.com/auth/realms/redhat-external/protocol/openid-connect/token
token=<automation_hub_token>
```

Set the `token` to the value you get after authentication on automation hub.

### 2. install dependencies

The following command will download and install the dependencies.

    # pip install -r requirements.txt
    # ansible-galaxy collection install -r requirements.yml

### 4. domain names and certificates

* Update the configuration to reflect your domain and certificate details for secure access.

### 5. edit the configuration

To edit the configuration, you would need to modify the ansible.cfg file and relevant playbook variables. This includes:

* Provide Ansible Automation Hub token in ansible.cfg
* Database information, and TLS certificates in the playbooks or group variables (typically located in group_vars/).
* Configuring other parameters like the domain names for Keycloak and Data Grid.

These configurations ensure the infrastructure is tailored to your specific setup requirements before provisioning and deploying.

### 7. run the deployment of data_grid and rhbk

Inside `playbooks/roles` path we have `deploy.yml` playbook to deploy data_grid and rhbk.

## License

[Apache License Version 2.0](https://github.com/ansible-middleware/rhbk-ha-cluster/blob/main/LICENSE)
