# AnsibleController
Generates with ansible the infrastructure for an ContinuousIntegration/Testing project.

## Install
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
echo -e "\n## Added by ansible controller script\ncd $HOME;" >> ~/.bashrc
. ~/.bashrc

git clone https://github.com/AlwaysTesting/AnsibleController.git 
cd AnsibleController;
```


## Run

## Licence

