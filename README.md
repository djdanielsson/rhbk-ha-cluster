# rhbk-datagrid-aws


Provision and deploy a Red Hat Build of Keycloak authentication service on multiple AWS regions via Ansible

### Use case of rhbk-datagrid-aws collection


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



### edit the configuration


### run the infra provisioning


### run the deployment of data_grid and rhbk

## License

[Apache License Version 2.0](https://github.com/ansible-middleware/rhbk-datagrid-aws/blob/main/LICENSE)
