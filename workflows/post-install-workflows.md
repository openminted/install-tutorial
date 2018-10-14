## Workflows service execution backend post installation instructions

### Requirements

* python 2.7
* python-virtualenv
* ansible 2.7 or later

and 

* an installed OMTD Galaxy editor instance.
* an installed OMTD Galaxy executor instance.

### Configure Galaxies

By following the instructions below you wil be able to a) configure the galaxy instances (executor, editor) to use the OMTD TDM component classification scheme 
and b) install omtd-importer which is a component that is used in workflows for transfering/downloading data from OMTD Storage.  

* Clone install-tutorial repository (if it has not already been cloned). 
```code=bash
$ git clone https://github.com/openminted/install-tutorial.git
```
* cd to the workflows folder.
```code=bash
$ cd install-tutorial/workflows
```
* Edit hosts and set the IP(s) of the VM(s) that host Galaxy executor and editor. 
Check if something has to be changed in group_vars/all; it is the file that contains all the
configuration parameters. Then run the ansible script that configures/installs everything that is required.
```code=bash
$ ansible-galaxy install tecris.maven
$ ansible-playbook -i hosts site.yaml
```
* 

### Install docker images for UIMA/GATE/OMTD web services

All TDM components in OMTD platform run as Docker containers. For components that are based on 
UIMA, GATE, and OMTD web services we have created three separate generic built-in Docker images. Each image 
contains an executor that is able to run any component created with one of the three respective frameworks (UIMA/GATE/OMTD web services).
The images should be available in at least one Docker Registry (public or private) so that it can it can be pulled from the node (VM) that is assigned 
the task to start the respective Docker container. 
