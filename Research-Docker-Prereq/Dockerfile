#Pulling from a pre-built image that contains the JDK and Ant
FROM frekele/ant:1.10.1-jdk8u141

#Install the pre-requisite software for silver and create the ~/bin and ~/silver folders
RUN apt-get update && apt-get install -y --no-install-recommends make && \
		mkdir bin && \
		mkdir silver && \
		rm -rf /var/lib/apt/lists/*
#Set the path to look at the newly created ~/bin
ENV PATH=$PATH:/root/bin/

#Entrypoint set to /bin/bash so that you don't have to type that in when running docker run -i
ENTRYPOINT /bin/bash
