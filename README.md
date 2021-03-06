### Docker Image for Silver, AbleC and Extension development
#### Built by Ankit Siva

The main intent of this project is to help new joiners of the MELT-UMN lab avoid the pain of setting-up that the interns of summer of '17 faced. This is to also help ensure a uniform platform for development to remove the "It works on my machine" excuse. This also allows for lightning fast development on any machine, without having to ssh into the lab computers. Finally, this will allow for quick submission and tinkering for purposes of conferences.

Requirement: Latest version of Docker

To install Docker, go to [Docker.com] (https://www.docker.com/community-edition#/download), find the correct version for your OS, and:
- For Windows or macOS click the `Get Docker` button
  * Follow the installation instructions and ensure Docker is running
- For Ubuntu/other Linux distributions, click the Resources tab and follow the instructions on the `Detailed Installation Instructions` page.
  * It is recommended that you also perform the post-installation steps if running Ubuntu, to ensure safety of your system.[Read](https://docs.docker.com/engine/installation/linux/linux-postinstall/) for instructions to prevent having to use sudo/have a user without root access use the docker engine from using (if on Ubuntu).


Ensure your Docker daemon is running by running one of the following commands:
- macOS and Windows:
```bash
$ docker run hello-world
```
- Ubuntu
```bash
$ sudo docker run hello-world
```

Once you have the Docker client set-up, follow steps as written below:

Important things to remember before continuing:
1. Containers are stateless and ephemeral, this means that code will be written on your local machine but can be compiled and its effects/running observed in the Container
2. For now, an important design choice has been made regarding how to update the version of Silver stored on the image. For now, it pulls the latest version on each rebuild. This means that the images would need to rebuilt after every change to the origin/master of Silver. This could be done by adding a step in the Continuous Integration process that is currently followed.
3. After an update, the images would need to be rebuilt only once, as opposed to every person in the MELT Lab running ./update and ./deep-rebuild after every major update to Silver.

Continue reading [here for users](Important Commands) of the containers and [here for the developers of the containers](./README-Developers.md)

Important commands:
1. To pull the image that you want to work with, run:
```bash
$ docker pull quay.io/meltumn/<name-of-image>
```

2. To run an interactive session (attaches the session to your current terminal session):
```bash
$ docker run -i -t melt-umn/<name-of-image>
```
[The image names are indicated under each heading below]  
[Explanation of flags: -i indicates interactive, -t indicates the named tag of the image to run]

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
$ docker run -i -t -v ~/extensions/<extension-name>:/root/extensions/<extension-name> melt-umn/able-c-dev
```
[Explanation of the new -v flag: denotes the volume to bind, usage is <from/full/path/to/src>:<to/full/path/to/dest>]  
As an example:
```bash
$ docker run -i -t -v ~/extensions/ableC-tensors:/root/extensions/ableC-tensors melt-umn/able-c-dev
```
This way, any change you make to your *local* copy of your code, it will be reflected automatically in the container's volume.
