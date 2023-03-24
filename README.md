# Coti Node Image Builder

This repository periodically checks the releases of the official [coti-node](https://github.com/coti-io/coti-node/releases) repository, and if a new release is found, a Docker image of the release is automatically built and pushed to [Dockerhub](https://hub.docker.com/r/atomnode/coti-node/tags). The advantage of doing this process in GitHub actions, is that not only is the code open-source and transparent, but the *builds* of the images themselves are too. These images are produced by a Coti community member, for the Coti community to use as they wish.

Please dig in to the code. If you have ideas or input for the Coti node images, please feel free to let me know or make a pull request.

# Which files are involved in the build process?

The contents of this repo are kept deliberately minimal, so as to make as few changes as possible to the base Coti node software. 

Below are the three files involved in the build process:

- [.github/workflows/update-image.yml](https://github.com/tj-wells/coti-node-images/blob/master/.github/workflows/update-image.yml) - The GitHub Action workflow file itself, that describes the build process
- [check-for-new-release](https://github.com/tomjwells/coti-node-images/blob/master/check-for-new-release) - A short python script called by update-image.yml, which checks that the latest Coti node version matches the latest Docker image tag.
- [create-properties](https://github.com/tj-wells/coti-node-images/blob/master/create-properties) - A script that generates a  `fullnode.properties` file from the environment variables. This is to be run in the Docker container before launching the main Coti node program. It also downloads the appropriate clusterstamp file for MainNet or TestNet when necessary.

# 🐳 Overview of the Build Process

This section gives a high-level overview of the build process executed by <a href="https://github.com/tj-wells/coti-node-images/blob/master/.github/workflows/update-image.yml" target="_blank">this workflow file</a>.

Most of the workflow file is common to any GitHub action that builds a container image and pushes it to a container registry. The main step of interest, in which slight modifications are made to the basic Coti node repository, is one called "Modify coti-node Repository", which performs only one change to the Coti repository, which is to copy in the file [create-properties](https://github.com/tj-wells/coti-node-images/blob/master/create-properties) before performing the build. This is done so that that script may be run on launching the container to create the `fullnode.properties` file from environment variables.

# Workflow runs that created previous images

Since there are many workflow runs in which no image is built, it can be difficult to find the workflow runs that actually created new Docker images. The table below is used to keep a log of the Docker images of each new version of the Coti software and the workflow runs that built them.

| Coti Node Version |                                          Workflow Run                                          |                                                                            Dockerhub Image                                                                             |
| :---------------: | :--------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|       [3.1.3](https://github.com/coti-io/coti-node/releases/tag/3.1.3)       | [4400299976](https://github.com/tomjwells/coti-node-images/actions/runs/4400299976) | [3.1.3](https://hub.docker.com/layers/atomnode/coti-node/3.1.3/images/sha256-f5f7e78d8e03fbda62f6840eda2efd2610db9029d0f60b3696bc5cf8b3d44a3f?context=repo) |

# Where can I see an example of this Docker image being used?

See [this repository](https://github.com/tomjwells/coti-node) for an example and accompanying guide that suggests a method for running a Coti node using Docker. This repository contains the `docker-compose` files I use to run my node.

# Stay Coti

Stay Coti. ️‍🔥

<p align="center"><a href="https://atomnode.tomoswells.com" target="_blank"><img src="https://media.discordapp.net/attachments/465686348234358804/1088843067425050784/atoms-3-01.png?width=852&height=850" style="width: 330px"></a></p>
