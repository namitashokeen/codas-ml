# Getting started

Every participant will receive a dedicated IP address and a password to login to the VM in Azure Cloud. We will use 2 different Azure instance types for the exercise involving Spark and TensorFlow.

## ssh to Azure VM

```bash
ssh student@<unique ip>
```

## Checkout the course repo

Checkout the course repository:

```bash
git clone https://github.com/ASvyatkovskiy/codas-ml
cd codas-ml
```

## Setup Spark-enabled Jupyter 

All VMs will have pre-installed Anaconda. 

Set environmental variables to launch Spark-enabled jupyter notebook.

```bash
export PYSPARK_PYTHON="/anaconda/bin/python2.7"
export PYSPARK_DRIVER_PYTHON="/anaconda/bin/jupyter"
export PYSPARK_DRIVER_PYTHON_OPTS="notebook --no-browser --port=8889 --ip=127.0.0.1"
```

and add them to your **.bashrc** so that you do not need to retype every time you open a command line window.

Next launch of pyspark shell will prompt you to the notebook:

```bash
pyspark [options]
```

where [options] is the list of flags you pass to pyspark (we have already specified the Jupyter's options!).

## Open Jupyter session in local web-browser

Once the Spark-enabled Jupyter notebook is up and running on your Azure VM, open a terminal window on your local machine (laptop) and establish an ssh-tunnel to the VM:

```bash
ssh -N -f -L localhost:8888:localhost:8889 student@<unique ip>
```

The first option -N tells SSH that no remote commands will be executed, and is useful for port forwarding. The second option -f has the effect that SSH will go to background, so the local tunnel-enabling terminal remains usable. The last option -L lists the port forwarding configuration (remote port 8889 to local port 8888).

Note: tunnel will be running in the background. The notebook can now be accessed from your web-browser at http://localhost:8888
When opened first time, it will ask for a secure token, which is printed on the screen in Azure VM session, use it.

## Make sure you have the right kernel

In Jupyter notebook, type "Kernels" button, select the **conda:root** environment - this will give you Anaconda Python 2.7.13. Double check you have the right version in by typing following in a cell:

```python
import sys
sys.version  #shift+enter to evaluate
```
