FROM ubuntu:14.04
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y git
RUN apt-get install -y g++
RUN apt-get install -y cmake
RUN apt-get install -y python-dev
RUN apt-get install -y python-numpy
RUN apt-get install -y python-pyparsing
RUN apt-get install -y python-nose
RUN apt-get install -y python-mpi4py
RUN apt-get install -y openmpi-bin
RUN apt-get install -y libopenmpi-dev
RUN apt-get install -y libhdf5-dev
RUN apt-get install -y libeigen3-dev
RUN apt-get install -y libgsl0-dev
RUN apt-get install -y python-tables
RUN apt-get install -y libboost-dev
RUN apt-get install -y libboost-python-dev
RUN apt-get install -y libboost-regex-dev
RUN apt-get install -y libboost-system-dev
RUN apt-get install -y libboost-filesystem-dev
RUN apt-get install -y libboost-iostreams-dev
RUN apt-get install -y libboost-test-dev
RUN apt-get install -y libboost-serialization-dev
RUN apt-get install -y vim
RUN useradd -ms /bin/bash synergia
USER synergia
WORKDIR /home/synergia
RUN git clone http://cdcvs.fnal.gov/projects/contract-synergia2 synergia2-devel
WORKDIR /home/synergia/synergia2-devel
RUN git checkout -b devel origin/devel && ./bootstrap
RUN ./contract.py --configure hdf5_internal=0 || /bin/true
RUN ./contract.py --configure eigen3_internal=0 || /bin/true
RUN ./contract.py fftw3 || /bin/true
RUN ./contract.py chef-libs || /bin/true
RUN ./contract.py || /bin/true

