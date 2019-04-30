FROM ubuntu:bionic

MAINTAINER 'Carlos H Brandt <carloshenriquebrandt at gmail>'

# Version of Saga-Gis in Git repository (i.e., 'git tag')
ARG SGG_GIT_VERSION='release-6-1-0'

ENV DEBIAN_FRONTEND='noninteractive'

RUN apt-get update && \
    apt-get install -qy libwxgtk3.0-dev libtiff5-dev libgdal-dev libproj-dev  \
                        libexpat-dev wx-common libogdi3.2-dev unixodbc-dev  && \
    apt-get install -qy g++ make automake libtool git                       && \
    apt-get clean

# Get last version of a git repo tag
# LAST_TAG=$(git tag | xargs -I@ git log --format=format:"%ai @%n" -1 @ | sort | awk '{print $4}')

RUN _TMPDIR=$(mktemp -d) && cd $_TMPDIR && \
    git clone git://git.code.sf.net/p/saga-gis/code saga-gis-code && \
    cd saga-gis-code/saga-gis/ && \
    git checkout $SGG_GIT_VERSION && \
    autoreconf -fi && \
    ./configure && \
    make && \
    make install && \
    cd && \
    rm -rf $_TMPDIR

RUN git clone -b stable https://github.com/chbrandt/docker_entrypoint.git && \
    ln -sf docker_entrypoint/entrypoint.sh /.

ENTRYPOINT ["/entrypoint.sh"]
