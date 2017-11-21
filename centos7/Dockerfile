FROM centos:7
RUN yum update -y
RUN yum install -y openmpi hdf5-devel python-devel cmake boost-devel openmpi-devel numpy mpi4py-openmpi python-tables gsl-devel eigen3-devel pyparsing git python-devel zlib-devel gcc-c++ bzip2 make
RUN yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN yum install -y eigen3-devel hdf5-devel python-ipython
RUN echo 'module load mpi/openmpi-x86_64' > /etc/profile.d/zz-openmpi.sh
RUN useradd -ms /bin/bash synergia
USER synergia
WORKDIR /home/synergia
RUN git clone http://cdcvs.fnal.gov/projects/contract-synergia2 synergia2-devel
WORKDIR /home/synergia/synergia2-devel
RUN git checkout -b devel origin/devel && ./bootstrap 
RUN . /etc/profile.d/modules.sh ; module load mpi/openmpi-x86_64 ; ./contract.py fftw3 || /bin/true
RUN . /etc/profile.d/modules.sh ; module load mpi/openmpi-x86_64 ; ./contract.py mpi4py || /bin/true
RUN . /etc/profile.d/modules.sh ; module load mpi/openmpi-x86_64 ; ./contract.py chef-libs  || /bin/true
RUN . /etc/profile.d/modules.sh ; module load mpi/openmpi-x86_64 ; ./contract.py || /bin/true

