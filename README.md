# COTI Node Docker Image Builder

This repository supplements the repository, <a href="https://github.com/tj-wells/coti-node" target="_blank">COTI Node Docker Installation Method</a>, which proposes a simple method for installing and maintaining Coti nodes using Docker containers.

This repository executes the build process of the coti-node images in an open-source and publicly transparent way, so that the images it generates can be trusted. In addition, others can produce their own images by cloning this repository and making variations.

# What does this Repository do?

This repository makes use of a Github actions workflow to check for new releases of the coti-node in the <a href="https://github.com/coti-io/coti-node">official coti-node repository</a> every morning and if a new version is available, it executes a build of the new release.

- To view the workflow file that performs the build process, <a href="https://github.com/tj-wells/coti-node-images/blob/master/.github/workflows/update-image.yml">click here</a>.
- To view the runs of the workflows themselves, <a href="https://github.com/tj-wells/coti-node-images/actions">click here</a>.
- To view the images built and pushed from this repository, <a href="https://hub.docker.com/repository/docker/atomnode/coti-node">click here</a>.

# Steps involved in the Build Process

This section provides a high-level overview build process executed by <a href="https://github.com/tj-wells/coti-node-images/blob/master/.github/workflows/update-image.yml">this workflow file</a>.

1. Download the new official Coti release.
2. Modify the `Dockerfile` to download the clusterstamp file.
3. Copy a script (`update-env`), which uses the container's environment variables to generates a new `fullnode.properties` file.

# Stay Coti

Stay Coti. ️‍🔥

<p align="center"><a href="https://twitter.com/tomjwells" target="_blank"><img src="https://cdn.discordapp.com/avatars/343604221331111946/65130831872c9daabdb0d803ce27e594.webp?size=240"></a></p>
