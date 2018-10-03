## Package requirements  
  
 - Docker 17.03 or later
    Instructions for docker installation can be found [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04). You can always follow our scripts, given below, and automate the installation.
  
## Scripts  
  
***Running the following scripts requires Ansible***
``sudo apt-get install ansible``


After cloning the project [install-tutorial](https://github.com/openminted/install-tutorial.git), you'll find under the directory registry all the files needed for the installation of   
OpenMinTeD registry.  
  
Firstly you need to split your VMs in manager and worker roles.  
***Only one manager/installation is allowed. Having a manager is obligatory**  
**Multiple workers can exist. However, OpenMinTeD can be installed with 0 workers defined***  
  
In order to set the manager/worker(s) you need to edit the ``/etc/ansible/hosts`` file and define the roles as follows:  
  
``[manager] `` 
`` IP_OF_TARGET ansible_user=USERNAME ansible_sudo_pass=PASSWORD_FOR_SUDO ansible_password=PASSWORD_FOR_SSH `` 
``[worker]``
 ``IP_OF_TARGET ansible_user=USERNAME ansible_sudo_pass=PASSWORD_FOR_SUDO ansible_password=PASSWORD_FOR_SSH 
``  
 
Add as many workers as you like, but remember, you need exactly one manager!

Next in line is executing the scripts under registry/scripts directory. The command for executing each script is ``ansible-playbook SCRIPTNAME``. 

The right order of execution is the following

 1. basic.yml
 
 *This script will install python(2) and your ssh-keys in all the VMs that are going to be used for the deployment of OpenMinTeD* 
 
 2. docker-install.yml
 
 *Following the above installation, this script will install docker in all the VMs*
 3. swarm-init.yml
 
 *This one will take care of the docker swarm initiation, setting manager and worker(s) nodes as defined and grouped in the /etc/ansible/hosts file*
 
 4. nfs-init.yml
 
*Executing "nfs-init.yml" will lead in mounting the drives/paths needed by galaxy to properly function.* 
***Executing this script requires granted access @ the network that galaxy is operating. Skipping the above will lead in a failure of execution.***
 5. update-stack.yml
 
 *Using this one will transfer all the necessary files in the target VM and will ensure that everything will be deployed in the swarm*.
 
 6. upload.yml
 
 *Finally this will populate the databases of OpenMinTeD registry with all the necessary data.*

