# Ansible configuration Management (Automate Project)

## Install and Configure Ansible on EC2 instance

* We can update the name tag of our Jenkins instance to Ansible Or just we can just create a new instance called ansible , we'll use the server to run a playbook

* in our github we'll create a new repository and name it ansible-config-mgt.

* Then we can start with installing ansible

```
sudo apt update # update the package manager

sudo apt install ansible # install ansible
```
---



* check the ansible version using the command ansible --version

* Note: Configure jenkins build job to archive your repository content everytime you change it - this will solidify our jenkins configuration skills acquired in the previous project

* Create a new freestyle project ansible in jenkins and point it to your ansible-config-mgt repository .

* Configure a webhook in Github and set the webhook to trigger ansible build.
* Configure a postbuild job to save all(**) files. like you did in the previous project.


+ Test your setup by makin some changes in your README.md file in the masters branch and make sure that builds start automatically and jenkins saves the file (build artifacts) in the following folder .

```
ls /var/lib/jenkins/jobs/ansible/builds/<build number>/archive/
```
+ Note: Trigger jenkins project execution only for main (or master) branch.

+ Note: Whenever you stop/start the jenkins/ansible server you will have reconfigure the Github webhook to a new IP address. in order to avoid it . in order to avoid this you'll allocate an Elastic IP to your jenkins/ansible server


---

#### The interesting about DevOps is that the first word the is "Dev" which you have to write some codes and have some tools that will make writing of those codes easy to use , deploy and debugging of those code comfortable as well.

+ Download a IDE of your choice and configure it to suite your style or need but as for me i use EMACS a Terminal/Graphical text editor .

+ Clone your ansible-config-mgt repo to your jenkins-ansible-instance .
```
git clone <ansible-config-mgt> repo link
```
