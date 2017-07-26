FROM frekele/ant

USER melt_umn_developer

WORKDIR /usr/

ENV PATH "/root/bin:$PATH"

RUN apt-get update && apt-get install -y git && \
		apt-get install --reinstall -y make && \
		mkdir bin && \
		PATH = $PATH:/root/bin && \
		mkdir silver

ENTRYPOINT /bin/bash
