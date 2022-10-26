## ANSIBLE REFACTORING AND STATIC ASSIGNMENTS (IMPORTS AND ROLES)

1. Install and configure Jenkins-Ansible server and create a new directory called ansible-config-artifact

`sudo mkdir /home/ubuntu/ansible-config-artifact`

`chmod -R 0777 /home/ubuntu/ansible-config-artifact`

2. Go to Jenkins web console -> Manage Jenkins -> Manage Plugins -> on Available tab search for Copy Artifact and install this plugin without restarting Jenkins

- Refactor Ansible code by importing other playbooks into site.yml

- Create a folder static assignments,move common.yml file into the newly created static-assignments folder,inside site.yml file, import common.yml playbook.

- Run ansible-playbook command against the dev environment


3. Configure UAT Webservers with a role Webserver

- Launch 2 fresh EC2 instances using RHEL 8 image, we will use them as our uat servers, so give them names accordingly – Web1-UAT and Web2-UAT.

- Create a role relative to the playbook file 

- Go into tasks directory, and within the main.yml file and configure

4. Reference Webserver role

- Within the static-assignments folder, create a new assignment for uat-webservers uat-webservers.yml. This is where you will reference the role.

- Commit your changes, create a Pull Request and merge them to master branch

- Run the playbook against your uat inventory 

`ansible-playbook -i /home/ubuntu/ansible-config-artiifact/inventory/uat.yml /home/ubuntu/ansible-config-artifact/playbooks/site.yml`

- Test uat-webservers on browser