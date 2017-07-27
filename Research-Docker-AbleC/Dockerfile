FROM melt-umn/silver-dev

WORKDIR /root/silver/support/nailgun

RUN	./install-sv-nailgun
WORKDIR /root

RUN	apt-get install -y gcc && \
		mkdir ableC && \
		mkdir extensions && \
		git clone https://www.github.com/melt-umn/ableC.git ableC

WORKDIR /root/ableC

RUN ./build

ENTRYPOINT /bin/bash 
