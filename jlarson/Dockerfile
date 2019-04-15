FROM ubuntu:16.04
RUN apt-get update && apt-get dist-upgrade -y
RUN apt-get install -y apt-utils
RUN apt-get install -y git
RUN apt-get install -y g++
RUN apt-get install -y cmake
RUN apt-get install -y python-dev
RUN apt-get install -y python-numpy
RUN apt-get install -y python-pyparsing
RUN apt-get install -y python-nose
RUN apt-get install -y python-tables
RUN apt-get install -y python-pip
RUN apt-get install -y python3.5
RUN apt-get install -u zlib1g-dev
RUN apt-get install -y libopenmpi-dev
RUN apt-get install -y openmpi-bin
RUN apt-get install -y libmpich-dev
#RUN update-alternatives --query mpi
RUN update-alternatives --set mpi /usr/include/mpich
RUN update-alternatives --set mpirun /usr/bin/mpirun.mpich
RUN apt-get install -y nano
RUN apt-get install -y bzip2
RUN apt-get install -y libgsl-dev
RUN apt-get install -y libhdf5-dev

RUN mkdir /nfs2
RUN useradd -ms /bin/bash -d /nfs2/jlarson jlarson
USER jlarson
WORKDIR /nfs2/jlarson
RUN pip install mpi4py
RUN git clone https://bitbucket.org/fnalacceleratormodeling/contract-synergia2 synergia2-devel
WORKDIR /nfs2/jlarson/synergia2-devel
RUN git checkout -b jlarson201904 origin/jlarson201904 && ./bootstrap
RUN ./contract.py --configure hdf5_internal=0
RUN ./contract.py boost
RUN ./contract.py fftw3
RUN ./contract.py chef-libs/git-clone

RUN ./contract.py chef-libs

RUN ./contract.py synergia2/git-clone
RUN ./contract.py synergia2/cmake
RUN ./contract.py

#RUN ./contract.py || /bin/true

