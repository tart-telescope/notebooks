# TART CASA calibration walkthrough

This repository contains the CASA/WSClean practical for the TART telescope deployment at Rhodes University
but can equally apply to other deployments and configurations. It demonstrates how standard tooling in 
CASA/WSClean can be used to process converted TART data (using the ```tart2ms``` package), stored in 
CASA memo 229 MSv2 specification format.

There are a few packages that have to be installed from your Debian (or equivalent) distribution repos:
- xvfb
- x11-utils
- cmake
- build-essential
- wget
- curl
- git
- python3
- libpython3-dev
- python3-pip
- fuse3
- libfuse2
- libopenmpi-dev
- openmpi-bin
- openmpi-common

You also need to install the WSClean imager from the latest KERN release for your Ubuntu distribution. For 20.04 LTS
this is [KERN 7](https://launchpad.net/~kernsuite/+archive/ubuntu/kern-7), or you need to compile from source.

The Python requirements, including CASA 6.5 can be installed via
```
pip install -r requirements.txt
```
Note: we strongly recommend doing this inside a virtual environment.

We have tested this for Python3.8 under Ubuntu 20.04. As it stands CASA 6.5 will not install properly
inside a docker container without escalated privileges, due to a requirement on FUSE mounts by plotms.
Part of the Python requirements.txt file will install an IPython kernel which can be linked deployed as a
standard Jupyter / JupyterHub kernel as follows. With a standard installation for the user this lives in 
${HOME}/.local/share/jupyter/kernels/casatart/kernel.json (you need to create the directories and files if
not existant).
```
{
 "argv": [
  "path_to_your_virtualenv/bin/python3",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "CASA TART",
 "language": "python"
}
```
