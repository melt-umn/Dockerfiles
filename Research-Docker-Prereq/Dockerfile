FROM frekele/ant

RUN apt-get update && apt-get install -y git && \
		apt-get install --reinstall -y make && \
		mkdir bin && \
		mkdir silver

ENV PATH=$PATH:/root/bin/

ENTRYPOINT /bin/bash
