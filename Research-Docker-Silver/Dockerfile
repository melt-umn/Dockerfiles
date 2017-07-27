#This uses a lightweight Debian, JDK, and Ant stack
FROM	melt-umn/silver-prereq 

#Creating a bin under the root directory
RUN	git clone https://github.com/melt-umn/silver.git silver/
		
WORKDIR /root/silver/support/bin

RUN		./install-silver-bin

WORKDIR /root/silver/

RUN ./update

RUN ./deep-rebuild

ENTRYPOINT /bin/bash
