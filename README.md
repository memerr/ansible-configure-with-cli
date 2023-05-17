Configure Juniper network devices with set commands
===========

Prerequisits:
-----
1. Enable netconf on a remote device:
```sh
set system services netconf ssh
```

2. Python3 - present in many current linux distros

3. Ansible 2.10 or later (required for the juniper.device collection) - https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

4. Pip3
```sh
which pip3
```
```sh
sudo apt install python3-pip
```
```sh
pip3 --version
```

5. Junos PyEZ 2.6 or later (junos-eznc) - https://www.juniper.net/documentation/us/en/software/junos-pyez/junos-pyez-developer/topics/task/junos-pyez-server-installing.html
```sh
sudo pip3 install junos-eznc
```
Make sure you've met all dependencies

6. The jxmlease Python module
```sh
pip3 install jxmlease
```

7. The xmltodict Python module (required for the juniper.device collection).
```sh
pip3 install xmltodict
```

8. JSNAPy 1.3.6 or later (required to use the jsnapy and juniper_junos_jsnapy modules).
```sh
pip3 install jsnapy
```

9. Ansible juniper.device collection
```sh
ansible-galaxy collection install juniper.device
```

10. Download files from this repository to the same directory

Usage
-----
1. Device credentials
- You specify the device credentials in cleartext in the playbook - just uncomment the vars section

or

- You can use file with credential variables defined as "admin_username" and admin_password in a yaml format defined in "vars_files" section.
example of auth-vars.yaml:
```sh
admin_username: username
admin_password: password
```
or 

- You can use an ansible-vault to encrypt credential files - https://www.juniper.net/documentation/us/en/software/junos-ansible/ansible/topics/topic-map/junos-ansible-authenticating-users.html#task-retrieve-password-vault

or

- You can use ssh keys/provider parameter when using Juniper.junos role - https://www.juniper.net/documentation/us/en/software/junos-ansible/ansible/topics/topic-map/junos-ansible-authenticating-users.html#task-juniper-junos-modules-provider-parameter

2. Running a play:
```sh
ansible-playbook pb-configure-with-set.yaml
```
