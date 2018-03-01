# AnsibleController für Debian Stretch
Generates with ansible the infrastructure for an ContinuousIntegration/Testing project.

## Install and prepare server
### Definition
server = CI-pipeline server

### Paketquellen
```
sudo bash // become root user
apt-get update
apt-get install git ansible
```
### Create project specific user and directory
```
adduser ansible --home /msr/people/<project specific user> --disabled-login; // create technical user
su <project specific user>;
echo -e "\n## Added by ansible controller script\ncd $HOME;" >> ~/.bashrc // go by login to project dir
. ~/.bashrc // load conf instantly
```
### Donload playbooks, roles and handlers
```
git clone https://github.com/AlwaysTesting/AnsibleController.git AnsibleController // this repo
cd AnsibleController // goto
```
### Connect and create credentials
For the first login to the server ansible needs credentials.
This script use therefore a user and a key. They will be *deleted* during installation.
Replace the ip adress, the user and the private key file in the _hosts_-file with the server ones.
There will be a prompt "No matching host key fingerprint found in DNS. Are you sure you want to continue connecting (yes/no)?". Type _yes_.
```
ansible pipe -m raw -a "echo server is online" // check if the server responses
```
Now there should be a green success message in the command prompt.
### Install python
Ansible needs python version 2 to run sucessfully. Maybe there will be a SUDO password prompt.
```
ansible pipe --sudo -K -m raw -a "apt-get update; apt-get install -y python python-simplejson"
ansible pipe -m ping // check python
```
## Playbooks
These playbooks were tested on Debian 9 so we recommend that you use Debian or Ubuntu.
## Update ansible
```
ansible-playbook -K updateAnsible.yml
```

The following playbooks require Ansible 2.4 or higher.
### Setup playbook
This playbook adds a NOPASSWD entry in the sudoers file, forbit ssh password authentification, creates a user _ansible_ and deletes the start user (inclusive home).
```
ansible-playbook -K run.yml
```
### Application playbook
This playbook installs docker and creates some containers (jenkins, ansible, git). The git will be initialized with this example project:  https://github.com/AlwaysTesting/ExampleProject.git. Jenkins will use this git to go on building this pipeline.
```
ansible-playbook run-application.yml
```

## Licence
...
