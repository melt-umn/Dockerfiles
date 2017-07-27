#From the image with silver
FROM melt-umn/silver-dev

#Set working directory to the nailgun folder for ableC testing
WORKDIR /root/silver/support/nailgun

#Install the nailgun
RUN	./install-sv-nailgun

#Set working directory to /root
WORKDIR /root

#Install the latest version of gcc, make new directories ableC and extensions,
#and clone the ableC repository
RUN	apt-get install -y gcc && \
		mkdir ableC && \
		mkdir extensions && \
		git clone https://www.github.com/melt-umn/ableC.git ableC

#Set working directory to the ableC folder
WORKDIR /root/ableC

#Build ableC and install the scripts
RUN ./build

ENTRYPOINT /bin/bash 
