FROM melt-umn/silver-dev
RUN	cd silver/support/nailgun && \
		./install-sv-nailgun && \
		cd /root && \
		apt-get install -y gcc && \
		mkdir ableC && \
		mkdir extensions && \
		git clone https://www.github.com/melt-umn/ableC.git ableC

ENTRYPOINT /bin/bash 
