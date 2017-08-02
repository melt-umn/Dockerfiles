#From the image with silver
FROM melt-umn/silver-dev

#Set working directory to the nailgun folder for ableC testing
RUN cd /root/silver/support/nailgun && \
#Install the nailgun
		./install-sv-nailgun && \
#Set working directory to /root
		cd /root && \
#Install the latest version of gcc, make new directories ableC and extensions,
#and clone the ableC repository
		apt-get update && apt-get install -y --no-install-recommends git gcc libc6-dev && \
		mkdir ableC && \
		mkdir extensions && \
		git clone https://www.github.com/melt-umn/ableC.git ableC && \
#Set working directory to the ableC folder
		cd /root/ableC && \
#Build ableC and install the scripts
		./build && \
		apt-get remove -y git
ENTRYPOINT /bin/bash 
