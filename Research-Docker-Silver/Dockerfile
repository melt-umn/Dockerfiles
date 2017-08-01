#From the pre-requisite software image
FROM	melt-umn/silver-prereq 

#Clone the Silver repository into the silver folder
RUN	apt-get update && apt-get install -y --no-install-recommends git && \	
		git clone https://github.com/melt-umn/silver.git silver/ && \
#Set working directory to the installation directory of silver
		cd /root/silver/support/bin && \
#Run the install file
		./install-silver-bin && \
#Set working directory to silver's folder
		cd /root/silver/ && \
#Update and deep-rebuild silver
		./update && \
		./deep-rebuild && \
		apt-get remove -y git 

ENTRYPOINT /bin/bash
