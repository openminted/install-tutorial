## Workflows service execution backend post installation instructions


### Congigure galaxy to use the OMTD component classification and install omtd-importer 

Clone install-tutorial repository (if it has not already been cloned). 
```code=bash
$ git clone https://github.com/openminted/install-tutorial.git
```

cd to the workflows folder.
```code=bash
$ cd install-tutorial/workflows
```

Edit hosts and set the IP of the VM that hosts Galaxy executor and editor. 
Then run the ansible script that configures/installs everything that is required.
```code=bash
$ ansible-galaxy install tecris.maven
$ ansible-playbook -i hosts site.yaml
```

### Install docker images for UIMA/GATE

...
