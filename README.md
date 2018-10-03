# OMTD Install Tutorial event

## Practical information

* **Place**: ARC, Athens, Grece.
* **Date**: 15 and 16 October 2018.
* **Contact**: Robert Bossy

## Goals

The objective of this tutorial is to give future contributors a better insight on the OpenMinTeD services architecture and internal workings. The format of this event will be hackathon/practical class in order to promote a hands-on approach.

Attendees will install the OpenMinTeD services modules and deploy them in their own servers. The process will allow them to grasp fully the architecture of OpenMinTeD, to give them the opportunity to get answers to technical questions, and to reveal points where they might contribute.

Note that the instances of OpenMinTeD installed during this event are not meant to provide text-mining services to the public. They rather serve as a test bed to each participant and potential contributor.

## Prerequisites

### Introduction
The OpenMinTeD platform, being developed by 2 different teams, is divided in two parts: the Registry (which contains the portal and its supporting services) and the Workflow execution part (which contains Galaxy and the execution backend). The installation documentation for the 2 parts is split in different repositories which we definitely plan to unify in the near future.

### Skills

This event is going to be technical and thus requires attendees to be familiar with the following activities and tools:

* Linux system administration
* Application containers (docker, docker swarm and apache mesos/chronos)
* Python

### Hardware

OpenMinTeD services requires a heavy hardware configuration. Please ensure you have a proper [set of servers](https://github.com/openminted/install-tutorial/blob/master/hardware-requirements.md) before attending.

### Software
All services are install in Ubuntu 16.04 LTS, using docker 17.03. For installation we are using ansible and python. You can find more details in the instructions about the Registry or the Workflow service.

### Registry
You can find instructions on how to install the Registry [here](https://www.google.com)

### Workflow execution
The workflow execution service can be installed in 2 ways: in a standalone server, without support for docker cluster and mesos, and the full blown installation with support for a cluster. You can find instructions for the standalone installation [here](https://github.com/openminted/omtd-standalone-setup) and for the full blown installation [here](https://github.com/openminted/omtd-stack-setup/blob/master/docs/deployment_guide.md)
