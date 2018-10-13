## Workflows service execution backend post installation instructions

### Requirements

* python 2.7
* python-virtualenv
* ansible 2.7 or later

### Configure Galaxies

By following the instructions below you wil be able to: 
* Configure the galaxy instances (executor, editor) to use the OMTD TDM component classification scheme 
* Install omtd-importer which is a component that is used in workflows for transfering/downloading data from OMTD Storage.  

Clone install-tutorial repository (if it has not already been cloned). 
```code=bash
$ git clone https://github.com/openminted/install-tutorial.git
```

cd to the workflows folder.
```code=bash
$ cd install-tutorial/workflows
```

Edit hosts and set the IP(s) of the VM(s) that host Galaxy executor and editor. 
Then run the ansible script that configures/installs everything that is required.
```code=bash
$ ansible-galaxy install tecris.maven
$ ansible-playbook -i hosts site.yaml
```

### Install docker images for UIMA/GATE

...
