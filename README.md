# rhbk-datagrid-aws


Provision and deploy a Red Hat Build of Keycloak authentication service on multiple AWS regions via Ansible

### Use case of rhbk-datagrid-aws collection

The primary use case of the `rhbk-datagrid-aws` collection is to install Red Hat Build of Keycloak (RHBK) with high availability (HA) across multiple AWS regions. This ensures that the authentication service is resilient, fault-tolerant, and capable of serving users even in the event of a regional failure. By leveraging AWS infrastructure, the collection automates the setup of RHBK in a highly available architecture, integrating with Data Grid for distributed caching and ensuring smooth, secure authentication.

### 0. prerequisites

* The two regions that will host the authentication service (ie. us-east-1 and us-west-2)
* An AWS account with permissions on `ec2` on said regions with default profile in $HOME/.aws/credentials that will be used to provision ec2 compute nodes
* A database service that can be accessed from the deployment regions; or otherwise, `rds` permissions on the AWS account so an Aurora service can be provisioned
* TLS certificates for the desired domain name to provide the authentication service

### 1. create ansible.cfg

```
[defaults]
remote_user=ec2-user
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


### 3. create key pair

This key pair will be used by ansible to connect to the EC2 instances.

* Paste the path to the private key in ansible.cfg option `private_key_file`
* Copy the public key file to `files/id_rsa_aws.pub`


### 4. domain names and certificates

* Update the configuration to reflect your domain and certificate details for secure access.

### 5. edit the configuration

To edit the configuration, you would need to modify the ansible.cfg file and relevant playbook variables. This includes:

* Setting the private_key_file path in ansible.cfg to allow Ansible to connect to EC2 instances.
* Specifying AWS regions, database information, and TLS certificates in the playbooks or group variables (typically located in group_vars/).
* Configuring other parameters like the domain names for Keycloak and Data Grid.

These configurations ensure the infrastructure is tailored to your specific setup requirements before provisioning and deploying.

### 6. run the infra provisioning

Inside `playbooks/roles` path we have `infra-up.yml` and `infra-down.yml` run both according to you need.

### run the deployment of data_grid and rhbk

Inside `playbooks/roles` path we have `deploy.yml` playbook to deploy data_grid and rhbk.

## License

[Apache License Version 2.0](https://github.com/ansible-middleware/rhbk-datagrid-aws/blob/main/LICENSE)
