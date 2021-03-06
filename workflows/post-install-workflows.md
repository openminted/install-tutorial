## Workflows service execution backend post installation instructions

### Requirements

In the control machine, i.e. the machine in which the ansible installation scripts will run.

* OS: Ubuntu 16.04 LTS
* python 2.7
* python-virtualenv
* ansible 2.7 or later

and 

* an installed OMTD Galaxy editor instance.
* an installed OMTD Galaxy executor instance.

### Configure Galaxies

By following the instructions below you will be able to run the ansible scripts that a) configure the galaxy instances (executor, editor) to use the OMTD TDM component classification scheme and b) install (on Galaxies) omtd-importer  which is a component that is used in workflows for transfering/downloading data from OMTD Storage.  

* In the control machine clone install-tutorial repository (if it has not already been cloned). 
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
*  Set the OMTD Storage service URL for omtd-importer in the respective shell script; the default path for this script in the 
standalone setup is /srv/executor/tools/omtdDataImport/omtdImport.sh

```
...
bash LinuxStartOMTDStoreClient.sh url http://<StorageServIP>:8090 downloadArch $omtdStoreCorpusID $zip;
...
```
 

### Galaxy access keys 
 Register and then log-in to Galaxy executor. The (default) url for accessing Galaxy executor in the standalone setup is 
 http://\<ExecutorIP\>/executor/. Go to the User tab -> Preferences -> Manage API key -> Create a new key. Write down the generated key.
 Also write down the remote_user_secret parameter value of Galaxy editor instance; you will find this parameter at galaxy.ini. In the case of standalone setup the default path for this is /srv/editor/config/galaxy.ini.
 

### Docker images 

All TDM components in OMTD platform run as Docker containers. For components that are based on 
UIMA, GATE, and OMTD web service frameworks we have created three separate generic built-in Docker images, respectively. 
Each one of these three images contains an OMTD executor that is able to run/call any component created with the respective framework (UIMA/GATE/OMTD web service); for more info on the images see [here](https://github.com/openminted/omtd-component-executor). 
All other OMTD TDM components should be dockerized by the providers according to the provided
[specs](https://github.com/openminted/omtd-docker-specification) and the respective images should be available at DockerHub.
The built-in images for UIMA/GATE/OMTD web service are already available at DockerHub.

```
galanisd/omtd-component-executor-omtd-ws:1.0.0
galanisd/omtd-component-executor-gate:8.5-SNAPSHOT
galanisd/omtd-component-executor-uima:2.10
```
### Notes

* In both workflow execution setups, standalone and mesos-based you can list the containers that have executed (in a VM) with `docker ps -a` and see the logs of a container by typing `docker logs <DOCKER CONTAINER ID>`. In the standalone setup all containers run in the machine that Galaxy is installed while in the Mesos-based in one of the Mesos nodes.

* The ansible configuration file [group_vars/all](https://github.com/openminted/install-tutorial/blob/master/workflows/group_vars/all) allows you to specify which GitHub repos/branches will be cloned and used (e.g. component_executor_repo and component_executor_version).  So it is possible to fork a repo that hosts a project create a different/customized version of it in a new branch, set the respective values in group_vars/all and have a custom installation.

* The Galaxy access keys and the docker image locations will be needed for configuring Registry installation.

