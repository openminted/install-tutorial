## Workflows service execution backend post installation instructions

### Requirements

* python 2.7
* python-virtualenv
* ansible 2.7 or later

and 

* an installed OMTD Galaxy editor instance.
* an installed OMTD Galaxy executor instance.

### Configure Galaxies

By following the instructions below you wil be able to: 
* Configure the galaxy instances (executor, editor) to use the OMTD TDM component classification scheme 
* Install omtd-importer which is a component that is used in workflows for transfering/downloading data from OMTD Storage.  

1.Clone install-tutorial repository (if it has not already been cloned). 
```code=bash
$ git clone https://github.com/openminted/install-tutorial.git
```

2. cd to the workflows folder.
```code=bash
$ cd install-tutorial/workflows
```

3. Edit hosts and set the IP(s) of the VM(s) that host Galaxy executor and editor. 
Check if something has to be changed in group_vars/all; it is the file that contains all the
configuration parameters. Then run the ansible script that configures/installs everything that is required.
```code=bash
$ ansible-galaxy install tecris.maven
$ ansible-playbook -i hosts site.yaml
```

### Install docker images for UIMA/GATE/OMTD web services

