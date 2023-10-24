# grokking-hpc
 a plebs guide to using TU Berlin's HPC


## Table of Contents
- [grokking-hpc](#grokking-hpc)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Connection and File Transfer](#connection-and-file-transfer)
  - [Installing Software](#installing-software)
  - [Job Management with SLURM](#job-management-with-slurm)
  - [Q\&A](#qa)
  - [Additional Resources](#additional-resources)

---

## Introduction
this documents aims to provide necessary understanding for the usage of HPC systems. It is not a comprehensive guide, but rather a collection of pointers to resources and tools that are useful for getting started.

an ssh connection to `gateway.hpc.tu-berlin.de` provides access to a frontend node with internet access. From there, one can transfer files, install software and connect to compute nodes and submit jobs to the SLURM scheduler. 

In this guide we will cover:
-  gaining access
-  transferring files
-  installing software
-  Job management



**System Architecture**
- Description of available hardware
- Conceptual introduction to frontend and compute nodes



## Connection and File Transfer

- **[VS Code Remote SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)**: enables remote editing of files and mounting of remote directories. Full VS Code functionality in remote environment.
- **tmux**: To manage multiple sessions. Sessions persist even if the connection is lost. [a guide](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
- **rsync**: For efficient file transfer. Can be used to sync directories.
  - **alternatives**: **scp** (secure copy), using **VS Code Remote SSH** or **sshfs** (mounting remote directories)



## Installing Software

- **module loader**: to load to modules available in the system you may use the following commands:
  - `module avail` to see the list of available modules
  - `module spider <module name>` to see available versions of a module
  - `module load <module name>` to load the module. You may also use 
  - `module unload <module name>` to unload a module


- **singularity**: singularity is a containerization tool that allows you to run software in an isolated environment. Since it doesn't require sudo, it is the preferred way of installing software. could be loaded with `module load singularity`
  - **[docker2singularity](https://github.com/singularityhub/docker2singularity)**: could be used for converting docker images to singularity images. [demo](https://github.com/stevekm/docker2singularity-demo)
    - **alternative**: using `singularity pull <docker://user/image:tag>` (pulls from docker hub) [link to doc](https://docs.sylabs.io/guides/3.2/user-guide/cli/singularity_pull.html)
- **miniconda**: For Python environment management. Comes with its own python and doesn't require sudo. Could be used for running python projects. [installation](https://docs.conda.io/projects/miniconda/en/latest/) &   [troubleshooting](https://github.com/dertilo/hpc-computing#3-setup-python-environment)




## Job Management with SLURM
HPC systems are shared resources. To manage the allocation of resources, a scheduler is used. The scheduler is responsible for allocating resources to jobs and managing the queue. SLURM (Simple Linux Utility for Resource Management) is an open-source job scheduler that allocates computational resources on a cluster for batch jobs and interactive sessions and used in our HPC system.
TODO: SLURM Guide





## Q&A
- How to get additional Modules?
  - ISIS forum has a request section
- Data management
  - how to manage large datasets?
    - git-lfs? pulling from tub cloud? pulling from gcp or aws?
- Picking the right tools
  -  distributing training across multiple GPUs?
  -  how to structure your code for parallelization?
  -  which resources are suitable for which tasks?
- monitoring and logging
  - how to monitor resource usage?
  - can one connect to compute nodes to monitor training? what if one is using multiple nodes?
- are Interactive sessions available?
- are there Quoatas?

## Additional Resources

[TUB HPC Documentation](https://hpc.tu-berlin.de/doku.php)

[ISIS Course](https://isis.tu-berlin.de/course/view.php?id=13680) (contains forum, intro slides, software requests)

[SLURM Cheat Sheet](https://hpc.uni.lu/old/users/docs/slurm_examples.html)

https://github.com/dertilo/hpc-computing

