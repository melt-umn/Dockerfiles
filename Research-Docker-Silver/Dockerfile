#From the pre-requisite software image
FROM	melt-umn/silver-prereq 

#Clone the Silver repository into the silver folder
RUN	git clone https://github.com/melt-umn/silver.git silver/
		
#Set working directory to the installation directory of silver
WORKDIR /root/silver/support/bin

#Run the install file
RUN		./install-silver-bin

#Set working directory to silver's folder
WORKDIR /root/silver/

#Update and deep-rebuild silver
RUN ./update

RUN ./deep-rebuild

ENTRYPOINT /bin/bash
