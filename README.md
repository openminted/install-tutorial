# OMTD Install Tutorial event

## Practical information

* **Place**: ARC, Athens, Grece.
* **Date**: ~~15 and 16 October 2018.~~
* **Contact**: Robert Bossy

## Goals

The objective of this tutorial is to give future contributors a better insight on the OpenMinTeD services architecture and internal workings. The format of this event will be hackathon/practical class in order to promote a hands-on approach.

Attendees will install the OpenMinTeD services modules and deploy them in their own servers. The process will allow them to grasp fully the architecture of OpenMinTeD, to give them the opportunity to get answers to technical questions, and to reveal points where they might contribute. Here's [a list of more concrete expectations](https://github.com/openminted/install-tutorial/blob/master/resources.md).

Note that the instances of OpenMinTeD installed during this event are not meant to provide text-mining services to the public. They rather serve as a test bed to each participant and potential contributor.


## Introduction/Prerequisites
The OpenMinTeD platform, being developed by 2 different teams, is divided in two parts: the Registry (which contains the portal and its supporting services) and the Workflow execution part (which contains Galaxy and the execution backend). The installation documentation for the 2 parts is split in different repositories which we definitely plan to unify in the near future.

### Skills

This event is going to be technical and thus requires attendees to be familiar with the following activities and tools:

* Linux system administration
* Application containers and container orchestration tools (e.g. docker, docker swarm and apache mesos/chronos)
* Python, Java

### Hardware requirements

The hardware requirements for OpenMinTeD platform depend on the version that is being installed. More information can be found  [here](https://github.com/openminted/install-tutorial/blob/master/hardware-requirements.md).

### Software requirements

OpenMinTeD platform installation has been automated using ansible and python.
You can find more details about the software requirements (e.g. OS) for the two OpenMinTeD parts, Registry and the 
Workflow execution in the respective instructions (see below).

## Installation Steps

### Workflow execution
The workflow execution backend service of OpenMinTeD can be installed in 2 ways: in a standalone server, without support for docker cluster and Chronos/Mesos, and the full blown installation with support for a Chronos/Mesos cluster. You can find instructions for the standalone installation [here](https://github.com/openminted/omtd-standalone-setup) and for the full blown installation [here](https://github.com/openminted/omtd-stack-setup/blob/master/docs/deployment_guide.md)

### Configure Workflow execution
After the workflow execution backend is installed and running, a number of extra steps must be performed. 
For more details see [here](https://github.com/openminted/install-tutorial/blob/master/workflows/post-install-workflows.md).

### Registry
You can find instructions on how to install the Registry [here](https://github.com/openminted/install-tutorial/blob/master/registry/README.md)

### Post installation steps
 Log in to the editor Galaxy and create a new user (any username and password will do). This will allow the nginx authentication headers to work correctly.

