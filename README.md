### Docker Image for Silver, AbleC and Extension development
#### Built by Ankit Siva

The main intent of this project is to help new joiners of the MELT-UMN lab avoid the pain of setting-up that the interns of summer of '17 faced. This is to also help ensure a uniform platform for development to remove the "It works on my machine" excuse. This also allows for lightning fast development on any machine, without having to ssh into the lab computers. Finally, this will allow for quick submission and tinkering for purposes of conferences.

Requirement: Latest version of Docker

Important things to remember:
1. Containers are stateless and ephemeral, this means that code will be written on your local machine but can be compiled and its effects/running observed in the Container
2. You will have to build each docker image the first time (until a local Docker registry is initialized or the images are uploaded to Dockerhub)

Important commands:
1. To build all the images, run build.sh in this directory with `$ make`, otherwise, copy the command to build the melt-umn/silver-prereq and melt-umn/silver-dev images if you don't need an image for AbleC development.
2. To run an interactive session (attaches the session to your current terminal session):
```bash
$ docker run -i -t melt-umn/<name-of-image>
```

Usage of a container at the lab can be broken down into 4 categories (as of Summer, 2017):
1. Working on Silver (Requires Silver)
2. Building a language (Requires Silver only)
3. Working on AbleC host C spec (Requires Silver and ableC)
4. Working on an Extension (Requires Silver and ableC)

The Dockerfiles that are used to build the images are distinguished based on use case, categorized above.

##### Working on Silver
*silver-dev*
For the purpose of working on Silver, a container with Silver and its pre-requisite software is installed. This includes:
1. Git (latest version)
2. Java Development Kit (From the Docker image frekele/ant)
3. Ant (From the Docker image frekele/ant)
4. Silver (latest stable release from Github)

##### Building a new language
*silver-dev*
This purpose has the same container as Silver. If you have additional requirements, add them to the Dockerfile for the specific container after reading the Docker docs.

##### Working on the ableC spec or an AbleC extension
*able-c-dev*
This comes with AbleC and an extensions folder to develop with.
Further, if you want to copy your code for an extension, run this command instead of the original:
```bash
docker run -i -t -v ~/extensions/<extension-name>:extensions/<extension-name> melt-umn/able-c-dev
```
As an example:
```bash
docker run -i -t -v ~/extensions/ableC-tensors:extensions/ableC-tensors melt-umn/able-c-dev
```

This way, any change you make to your *local* copy of your code, it will be reflected automatically in the container's volume.
