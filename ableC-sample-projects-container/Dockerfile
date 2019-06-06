# Use a parent image that contains the JDK and Ant
# This is the same that is done in the silver prereqs Docker for Silver development
FROM frekele/ant:1.10.1-jdk8u141

# NOTE: JFD stands for just for development  and represents lines commented out 
#       because they aren't necessary for just running and compiling the sample
#       projects.

ARG SILVER_BRANCH="feature/treesitter"
ARG SILVER_IDE_BRANCH="master"
ARG ABLEC_BRANCH="feature/ide_support"
ARG SILVER_ABLEC_BRANCH="feature/treesitter"
ARG EXT_IDE_BRANCH="feature/ide-support"
ARG EXT_BRANCH="develop"
ARG SAMPLE_PROJECT_BRANCH="feature/ide-support"

    # get dependencies
RUN apt-get update && apt-get install -y --no-install-recommends make git gcc libc6-dev sudo
RUN mkdir bin && rm -rf /var/lib/apt/lists/*
    # download silver
RUN git clone -b ${SILVER_BRANCH} https://github.com/melt-umn/silver.git
    # get the latest jars
RUN cd silver && ./update
    # rebuild silver composed jar on this branch
    # JFD ./self-compile && cp build/silver.composed.Default.jar jars/ && \
    # remove symbolic links if they exist then install silver to bin directory
RUN rm -f ~/bin/silver ~/bin/silver-custom && cd silver && ./support/bin/install-silver-bin
    # get silver ide tools
    # JFD git clone -b ${SILVER_IDE_BRANCH} && \

    # get ableC    
RUN git clone -b ${ABLEC_BRANCH} https://github.com/melt-umn/ableC.git
    # get extensions
RUN mkdir -p extensions && cd extensions && \
    git clone -b ${EXT_IDE_BRANCH} https://github.com/melt-umn/ableC-algebraic-data-types.git && \
    git clone -b ${EXT_IDE_BRANCH} https://github.com/melt-umn/ableC-cilk.git && \
    git clone -b ${EXT_IDE_BRANCH} https://github.com/melt-umn/ableC-regex-lib.git && \
    # get extensions that do not have ide support yet
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-check.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-checkTaggedUnion.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-closure.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-condition-tables.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-constructor.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-halide.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-interval.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-nonnull.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-prolog.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-refcount-closure.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-regex-pattern-matching.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-rewriting.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-sqlite.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-string.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-templating.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-template-algebraic-data-types.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-tensor-algebra.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-unification.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-vector.git && \
    git clone -b ${EXT_BRANCH} https://github.com/melt-umn/ableC-watch.git && \
    # get silver-ableC
    git clone -b ${SILVER_ABLEC_BRANCH} https://github.com/melt-umn/silver-ableC.git && \
    cd silver-ableC && ./fetch-jars && ./support/bin/install-silver-bin
    # get the sample projects
# Dont get sample projects use mounted version on your own file system
#RUN git clone -b ${SAMPLE_PROJECT_BRANCH} https://github.com/melt-umn/ableC-sample-projects.git

    
# get the cilk libraries
RUN echo "Downloading Cilk libraries" && \
wget -q http://melt.cs.umn.edu/downloads/cilk-usr_local.tar.gz && \
tar zxf cilk-usr_local.tar.gz && \
sudo mkdir -p /usr/local/include/cilk && \
sudo chmod o+rx /usr/local/include/cilk && \
sudo cp cilk-usr_local/include/cilk/* /usr/local/include/cilk/ && \
sudo chmod o+r /usr/local/include/cilk/* && \
sudo mkdir -p /usr/local/lib/cilk && \
sudo chmod o+rx /usr/local/lib/cilk && \
sudo cp cilk-usr_local/lib/cilk/* /usr/local/lib/cilk/ && \
sudo chmod o+r /usr/local/lib/cilk/* && \
sudo cp cilk-usr_local/lib/lib* /usr/local/lib/ && \
sudo chmod o+r /usr/local/lib/lib* && \
rm -rf cilk-usr_local*

# add home bin directory to the path
ENV PATH=$PATH:/root/bin

ENTRYPOINT /bin/bash
