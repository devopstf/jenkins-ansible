# Jenkins as a Service - Docker & Docker-compose
With this project you'll be able to generate your own Jenkins docker container from scratch (using the [jenkins-docker](https://github.com/devopstf/jenkins-docker) repository to generate the images locally with '*make*'), thanks to a specific ansible role used to generate dinamically the folders, the docker-compose file, as well as the service manager (systemd) file.

## Installation Guide
So, you've decided to install yourself a Jenkins docker container and control it through a systemd service!
Sometimes you can't invest the required time in doing so, and that's why this project exists!

### Pre-requisites
We'll need the following installed in our host machine:
- [Docker](https://www.docker.com/get-docker)
- [Ansible](https://www.ansible.com/)
- [Docker-compose](https://docs.docker.com/compose/install/) - *We recommend to place it on '/usr/bin'*
- [Make](https://www.gnu.org/software/make/)
- [Systemctl](https://www.freedesktop.org/software/systemd/man/systemctl.html)

### Set up your environment!
This project comes with everything you need, but you can modify it as you like: there's a '**vars**' folder with a *vars-jenkins.yml* file.

Here you can edit the variables used by ansible to setup your environment so everything goes as you like.

### Time to execute our Ansible role!
Once you've set up the variables matching your environment, it's time to begin. Just execute: `ansible-playbook playbook.yml`

And that's it!
Take in consideration that the first execution will take some time as it'll build the images locally.

Once it has finished, you'll have your Jenkins already installed and working as a service. You'll only need to manage it through systemctl: `systemctl {start|stop|restart} jenkins`

### Reconfigure anytime!

You'll be able to reconfigure the docker-compose, jenkins.service files by changing the *vars-jenkins.yml* file and executing the playbook again: the role will stop the service and reconfigure everything to match the new configuration!
