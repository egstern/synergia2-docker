FROM centos:6
RUN yum install -y openmpi hdf5-devel python-devel cmake boost-devel openmpi-devel numpy mpi4py-openmpi python-tables gsl-devel eigen3-devel pyparsing git python-devel zlib-devel gcc-c++ 
RUN echo 'module load openmpi-x86_64' > /etc/profile.d/zz-openmpi.sh
RUN useradd -ms /bin/bash synergia
USER synergia
WORKDIR /home/synergia
RUN git clone http://cdcvs.fnal.gov/projects/contract-synergia2 synergia2-devel
RUN cd synergia2-devel && git checkout -b devel origin/devel && ./bootstrap 
RUN cd synergia2-devel && ./contract.py || /bin/true

