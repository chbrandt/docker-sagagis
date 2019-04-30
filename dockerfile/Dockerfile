FROM ubuntu:bionic

    1  apt-get update
    2  apt-get install libwxgtk3.0-dev libtiff5-dev libgdal-dev libproj-dev     libexpat-dev wx-common libogdi3.2-dev unixodbc-dev
    3  apt-get install g++ make automake libtool git
    4  mkdir /home/devel
    5  cd /home/devel
    6  git clone git://git.code.sf.net/p/saga-gis/code saga-gis-code
    7  cd saga-gis-code/saga-gis/
    8  autoreconf -fi
    9  ./configure
   10  make
   11  make clean
   12  make distclean
   13  git branch
   14  git tags
   15  git tag
   16  git tag --help
   17  git tag --sort=committerdate
   18  git tag --sort
   19  git tag | xargs -I@ git log --format=format:"%ai @%n" -1 @ | sort | awk '{print $4}'
   20  git checkout release-6-1-0
   21  autoreconf -fi
   22  ./configure
   23  make
   24  make install
   25  history 

