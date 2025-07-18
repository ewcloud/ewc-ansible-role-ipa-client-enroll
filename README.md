# EWC Ansible Role IPA Client

This repository contains a configuration template 
(i.e. an [Ansible Role](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html)) 
to customize your environment in the
[European Weather Cloud (EWC)](https://europeanweather.cloud/).
The template is designed to:
* Configure a pre-existing RockyLinux or Ubuntu virtual machine to
connect to an IPA server running on the same subnet, such that it:
  * Is able to leverage DNS resolution and discover other private 
hosts or public addresses
  * Is remotely accessible via public key or password to centrally
managed LDAP users

## Copyright and License
>💡 No dependencies are distributed as part of this repository.

See the [LICENSE](./LICENSE) file for licensing information as it pertains to
files in this repository.

## Usage

The step-by-step described below assume your local file system follows the 
example structure below, with `ewc-ansible-role-ipa-client` being a clone of this
repository:
```
.
├── roles
│   └── ewc-ansible-role-ipa-client
├── inventory.yml
└── playbook.yml
```

### 1. Specify the target host and SSH credentials
Create an inventory file to specify address/credentials that Ansible should use
to reach the virtual machine you wish to configure:
```yaml
# inventory.yml
---
ewcloud:
  hosts:
    ipa_client:
      ansible_python_interpreter: /usr/bin/python3
      ansible_host: <add the IPV4 address of the target host>
      ansible_ssh_private_key_file: <add the path to local SSH RSA private key file>
      ansible_user: <add the username which owns the SSH RSA private key >
```
### 2. Customize the template

Edit input values for the template [variables](./vars/main.yml) as needed (see
[Inputs](#inputs) section for details).
Then, proceed to create an Ansible Playbook file to load your customizations: 

```yaml
# playbook.yml
---
- name: Deploy IPA Client on RockyLinux 8 or Ubuntu 22
  hosts: ipa_client
  become: true
  become_user: root
  become_method: ansible.builtin.sudo

  roles:
    - ewc-ansible-role-ipa-client

```

### 3. Apply the template


You can apply changes on the target host by running:
```bash
ansible-playbook -i inventory.yml playbook.yml
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| password_allowed_ip_ranges | IP ranges (in CIDR format) to be allowed for password access in SSHD configuration. Example: `['10.0.0.0/24', '127.0.0.1']` | `list(string)` | n/a | yes |
| ipa_client_hostname | IPA client host name. Example: `<openstack instance name>` | `string`| n/a | yes |
| ipa_domain |The IPA domain name. Example: `<memberstate>-<organization>-<projectname>.ewc` | `string` | n/a | yes |
| ipa_admin_password | The IPA Directory Manager/Admin password (at least 8 characters long) | `string` | n/a | yes |
| ipa_admin_username | Username of administrator account to replace the default IPA admin | `string` | n/a | yes |
| ipa_server_hostname | IPA server host name. Example: `ldap` | `string`| n/a | yes |


## Final Environment

### RockyLinux 8 Environment

Applying this template will trigger the installation of the following 
open-source packages onto your desired target RockyLinux host:

| Name | Version | License | Package Info |
|------|---------|---------|--------------|
| sssd | 2.9 | PLv3+ | https://github.com/SSSD/sssd |
| sssd-tools | 2.9 | GPLv3+ | https://github.com/SSSD/sssd |
| authselect | 1.2 | GPLv3+ | https://github.com/authselect/authselect |
| oddjob | 0.34 | BSD | https://pagure.io/oddjob |
| oddjob-mkhomedir | 0.34  | BSD | https://pagure.io/oddjob |
| ipa-client | 4.9 | GPLv3+ | http://www.freeipa.org |
| NetworkManager | 1.40 | GPLv2+ | https://networkmanager.dev/ |

### Ubuntu 22 Environment

Likewise, on your desired target Ubuntu host, the template will trigger 
installation of the following open-source packages:

| Name | Version | License | Package Info |
|------|---------|---------|--------------|
| sssd | 2.6 | GPLv3+ | https://github.com/SSSD/sssd |
| sssd-tools | 2.6 | GPLv3+ | https://github.com/SSSD/sssd |
| libnss-sss  | 2.6 | GPLv3+ | https://github.com/SSSD/sssd |
| libpam-sss | 2.6 |  GPLv3+ | https://github.com/SSSD/sssd |
| oddjob | 0.34 | BSD | https://pagure.io/oddjob |
| oddjob-mkhomedir | 0.34 | BSD | https://pagure.io/oddjob |
| ipa-client | 4.9 | GPLv3+ | http://www.freeipa.org |
| cracklib-runtime | 2.9 | - | https://github.com/cracklib/cracklib |
| nfs-common | 2.6 | - | https://linux-nfs.org |
| chrony | 4.2 | GPLv2+ | https://chrony.tuxfamily.org |


## Changelog
All notable changes (i.e. fixes, features and breaking changes) are documented 
in the [CHANGELOG.md](./CHANGELOG.md).

## Contributing

Thanks for taking the time to join our community and start contributing!
Please make sure to:
* Familiarize yourself with our [Code of Conduct](./CODE_OF_CONDUCT.md) before 
contributing.
* See [CONTRIBUTING.md](./CONTRIBUTING.md) for instructions on how to request 
or submit changes.

## Authors

[European Weather Cloud](http://support.europeanweather.cloud/) 
<[support@europeanweather.cloud](mailto:support@europeanweather.cloud)>
