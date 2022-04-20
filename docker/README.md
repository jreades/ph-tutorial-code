# Using Docker

You will need [Docker](https://www.docker.com) (Desktop) to be able to install the Programming Historing computing environment that we’ve created. If you do not wish to create an account with Docker then you may want to follow advice [provided here](https://github.com/docker/docker.github.io/issues/6910#issuecomment-532393783) though we cannot condone it.

#### Installing

Once you’ve installed the Docker application you can then install this container by opening up a Shell/Terminal and simply running:

> `docker pull jreades/ph:latest` 

**Note**: if you wanted a specific version of the image then you could change the `latest`  bit to the version that you want. You can see the list of available images here: [hub.docker.com/repository/docker/jreades/ph](https://hub.docker.com/repository/docker/jreades/ph)

#### Running

> **Note**: if you are using a **M1 Mac** then you probably need to add `--platform linux/amd64` option to the run commands below. I don't know if this will work as I don't have a M1 Mac to test.

The container can be run in the Shell or Terminal as:

> `docker run --name ph --rm -ti -p 8888:8888 -v "$(pwd):/home/jovyan/work" jreades/ph:latest jupyter lab --LabApp.password='' --ServerApp.password='' --NotebookApp.token=''`

**Note**: the `pwd` in the command above means use the _current_ directory. So if you simply open a Terminal, Git Bash, or Command Prompt then Docker will 'mount' (_i.e._ make visible to the programming environment) the current directory as `work` in the programming environment. This is most likely to be your home directory and means that _everything_ in your home directory is potentially delete-able or write-able and that is a major security risk. I would _strongly_ suggest that you `cd` (Change Directory) to a sub-folder along the lines of `./Documents/code/` so that you have the link `work <-> code` between the virtual machine that Docker is running and your computer (which is the 'host'). Obviously, this assumes that you've created a `code` directory in your Documents folder and you can revise according to what you have done instead!

Anyway, assuming that you have run the command above exactly as explained, then you will then be able to point your browser to [localhost:8888](localhost:8888/lab?). This will open up the JupyterLab interface.

A couple of notes on the command above:

* This opens the `8888` port of the container, so to access the Lab instance,
  you will have to point your browser to [`localhost:8888`](localhost:8888/lab/) Note that there is no space between `localhost` and `8888`, just a colon (`:`).
* The command also mounts the current folder (`pwd`) for the container, but you can replace that with the path to any folder on your local machine; for instance, on a Mac you could use something like `-v "/Users/<your username>/Documents/ph:/home/jovyan/work"` instead and then this would _always_ link the `ph` folder to `work` in the programming environment; however, I'd suggest that you wait until you understand how paths work before attempting to change this).
* The `name` ensures that you don't accidentally run three versions of the same Docker image!

#### Deleting

Should you wish to remove the image and container from your system then the following approaches are available:

##### Deleting by Filter

This should be used with some care since it will try to delete all matching images and this may not be what you want:

```bash
docker ps -aqf "name=ph" --format="{{.Image}} {{.Names}} {{.ID}}" | cut -d' ' -f3 | xargs docker rm -f
docker images --format="{{.Repository}} {{.Tag}} {{.ID}}" | grep "ph" | cut -d' ' -f3 | xargs docker rmi
```

##### Deleting by Image

```bash
docker ps -aq # Get list of running processes and work out container IDs to remove
docker rm -f <list of container IDs>
docker images # Get list of available images and work out image IDs to remove
docker rmi -f <list of image IDs>
```

## Citing

This draws on Dani Arribas-Bel's foundational work for the University of Liverpool. If you use this, you should also cite him.

[![DOI](https://zenodo.org/badge/65582539.svg)](https://zenodo.org/badge/latestdoi/65582539)

```bibtex
@software{hadoop,
  author = {{Dani Arribas-Bel}},
  title = {\texttt{gds_env}: A containerised platform for Geographic Data Science},
  url = {https://github.com/darribas/gds_env},
  version = {3.0},
  date = {2019-08-06},
}
```
