# AnsibleController
Generates with ansible the infrastructure for an ContinuousIntegration/Testing project.

## Install
### Definition
server = CI-pipeline server

### Paketquellen
Bitte den jeweiligen Paketmanager des Betriebsystems nutzen. Auf Debian basierenden Systemen ist meistens "apt" vorinstalliert:
```
apt-get install git
apt-get install ansible
```
### Environment and repository
```
sudo bash // become root user
adduser ansible --home /msr/<project specific user> --disabled-login; // create technical user
su <project specific user>;
echo -e "\n## Added by ansible controller script\ncd $HOME;" >> ~/.bashrc // go by login to project dir
. ~/.bashrc // load conf instantly
```
For the ssh connection you need to put the receive key to ~/.ssh/id_rsa(|.pub).
If you didn't get a key, generate one with `ssh-kegen` and copy the public key to the server.
```
git clone https://github.com/AlwaysTesting/AnsibleController.git 
cd AnsibleController;
```
Edit the hosts file:
* Replace &lt;cipipeline-host&gt; with the server domainname or ip address 
* Replace &lt;ssh-user&gt; with the predefined user on the server
### Prepare the server
```
ansible source --sudo -m raw -a "apt-get install -y python python-simplejson" // installs required packages for ansible
```


## Run

## Licence

