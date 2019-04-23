# Ansible automation for Jenkins on Vagrant instance

## TL;DR features
- Jenkins server with docker and pipeline support
- Tweak variables in: roles/jenkins/defaults/main.yml
- Add new jobs to: roles/jenkins/files/jobs
- By default jenkins runs on port 8085
- No authorization needed
- No manual configuration required

## Dependencies
- Vagrant
- Ansible >= 2.0

## How to run? 
- Check out repo
- Make sure to have installed the dependencies
- Run `vagrant up jenkins`
- Run Ansible: `ansible-playbook -i inventory site.yml -k -b -K -u vagrant` 
Password: `vagrant`

## Full description

`inventory`: 
- defines servers

`site.yml`:
- assigns roles

`Vagrantfile`:
- Configures basic ubuntu vm with private ip: 10.2.2.2

`roles/jenkins/defaults/main.yml`:
- all the variables used by Jenkins are here

`roles/jenkins/tasks/install.yml`:
- configures java, jenkins, docker installation
- Adds global config and jobs configs

`roles/jenkins/tasks/install-plugins.yml`:
- installs plugins through Jenkins API

`roles/jenkins/files/global-config.xml`:
- main configuration file for Jenkins (altered to disable security)

`roles/jenkins/files/jobs/super-duper-app`:
- Jenkins job config. Creates a remote-pipeline project. 
- Pipeline for java app deployed to docker demonstration [here](https://github.com/modcatz/bb-app/)


