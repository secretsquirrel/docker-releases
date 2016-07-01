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
    libcurl4-openssl-dev 

 
RUN pip install capstone pefile

RUN git clone https://github.com/secretsquirrel/the-backdoor-factory.git

WORKDIR "/the-backdoor-factory"
RUN git pull

WORKDIR "/the-backdoor-factory/osslsigncode"
RUN  ./autogen.sh \
     && ./configure \
     &&  make \
     && make install 

WORKDIR "/the-backdoor-factory/aPLib/example"

RUN gcc -c -I../lib/elf -m32 -Wall -O2 -s -o appack.o appack.c -v \ 
    && gcc -m32 -Wall -O2 -s -o appack appack.o ../lib/elf/aplib.a -v \ 
    && cp ./appack /usr/bin/appack        

WORKDIR "/the-backdoor-factory"

