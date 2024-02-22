# rhbk-datagrid-aws


### 0. prerequisites

* An AWS account with permissions on `ec2` and `rds` with default profile in $HOME/.aws/credentials
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

    # pip install -r requirements.txt
    # ansible-galaxy collection install -r requirements.yml


### 3. create key pair

* Paste the path to the private key in ansible.cfg option `private_key_file`
* Copy the public key file to `files/id_rsa_aws.pub`


### 4. domain names and certificates



### 4.
