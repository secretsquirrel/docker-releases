FROM ubuntu:15.04

RUN apt-get update && apt-get -y install \ 
    python-pip \
    autoconf \
    libtool \
    git \
    curl \
    libc6-dev-i386 \
    libtool \
    pkg-config \
    openssl \
    libssl-dev \
    libcurl4-openssl-dev \
    python-dev \ 
    libffi-dev \
    libxml2-dev \
    libxslt1-dev \
    libjpeg8-dev \
    zlib1g-dev


RUN pip install capstone pefile configobj

RUN pip install mitmproxy==0.17

RUN git clone https://github.com/secretsquirrel/bdfproxy.git

WORKDIR "/bdfproxy"

RUN git submodule init && git submodule update

WORKDIR "/bdfproxy/bdf"

RUN git pull origin master

WORKDIR "/bdfproxy/bdf/osslsigncode"

RUN  ./autogen.sh \
     && ./configure \
     &&  make \
     && make install 

WORKDIR "/bdfproxy/bdf/aPLib/example"

RUN gcc -c -I../lib/elf -m32 -Wall -O2 -s -o appack.o appack.c -v \ 
    && gcc -m32 -Wall -O2 -s -o appack appack.o ../lib/elf/aplib.a -v \ 
    && cp ./appack /usr/bin/appack        

WORKDIR "/bdfproxy/"

