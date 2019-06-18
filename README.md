# idia-container-jupytercasa

This repo contains the recipe for a [Singularity](https://www.sylabs.io/) container for [CASA](https://casa.nrao.edu/) version 5.5 for reducing radio data in a [Jupyter](https://jupyter.org/) notebook. Instructions for installing Singularity can be found [here](https://www.sylabs.io/guides/3.0/user-guide/installation.html#installation). The container was developed by the Inter-University Institute for Data Intensive Astronomy (IDIA) in [this repository](https://github.com/idia-astro/idia-container-jupytercasa) and forked here for updating to the latest version of CASA and pushed to [Singularity Hub](https://www.singularity-hub.org/).

## Installation

Simply download the image from [Singularity Hub](https://www.singularity-hub.org/collections/3164) by executing:

```
$ singularity pull --name idia-jupyter-casa-5.5.simg shub://rainsworth/idia-container-jupytercasa
```


## Usage

You can interact with this image in several ways:

#### Shell

Use the [shell](https://www.sylabs.io/guides/3.0/user-guide/quick_start.html#shell) command to spawn a new shell within the container and interact with it as though it were a small virtual machine by executing

```
$ singularity shell --cleanenv --home $PWD idia-jupyter-casa-5.5.simg 
```

#### Run

Use the [run](https://www.sylabs.io/guides/3.0/user-guide/quick_start.html#running-a-container) command to trigger the [runscript](https://www.sylabs.io/guides/3.0/user-guide/definition_files.html#runscript), which has been setup to execute a CASA script provided as an argument with the following synopsis: ```singularity run [CONTAINER] [SCRIPT] [ARGS] ``` where the [ARGS] are any arguments to pass to the script. For example, execute:

```
$ singularity run --cleanenv --home $PWD idia-jupyter-casa-5.5.simg script.py
```

#### Exec

The [exec](https://www.sylabs.io/guides/3.0/user-guide/quick_start.html#executing-commands) command allows you to execute a custom command within a container by specifying the image file. For example, to execute a CASA script:

```
$ singularity exec --cleanenv --home $PWD idia-jupyter-casa-5.5.simg casa -c script.py 
```

---

Action flags:

- ```--cleanenv```: Clean the environment before running the container. Can also use: ```-e```.
- ```--home $PWD```: home directory specification, in this case the current working directory outside the container becomes the home directory within the container. Can also use: ```-H <spec>```
- ```--bind data.ms:$HOME```: binds data.ms on the host to $HOME in the container. Can also use: ```-B <spec>```.

For more flags, execute ``` singularity exec help```.
