### Instructions for Container Developers
#### Written by Ankit Siva

Important: Read this only after you have downloaded, are able to run Docker, and you are going to *develop* containers.

Steps to Docker Mastery:
1. Read and complete the [Docker Getting Started guide](https://docs.docker.com/get-started/).
2. Read and familiarize yourself with the Dockerfiles that have been provided.
3. Read about the [best practices](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/#).
4. Begin development keeping in mind the important notes given below:

Docker images are stored on [Quay.io](https://quay.io/meltumn/) and images are triggered to build after every push to the head of the [Quay.io-auto-build](https://github.com/melt-umn/Dockerfiles/tree/quay.io-auto-build) branch.

To edit the build triggers and other settings of how the images are stored on Quay.io, you will need a Quay.io account. This is easily obtained by authorizing Github.com authentication. If you do not have a Github.com account, follow the procedure for another way to authenticate. Note that you will need a github.com account to contribute to the Dockerfiles repository.

Once done with this, ask Dr. Van Wyk to add you as a member of the team.

To change build triggers, look at `quay.io/repository/meltumn/<repository name>?tab=builds`

You can also start new builds without pushing to the repository.
