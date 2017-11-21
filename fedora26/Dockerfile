FROM fedora:26
RUN dnf update -y
RUN dnf install -y openmpi hdf5-devel python-devel cmake boost-devel openmpi-devel numpy mpi4py-openmpi python-tables gsl-devel eigen3-devel pyparsing git python-devel zlib-devel gcc-c++ bzip2 make eigen3-devel hdf5-devel python-ipython python2-mpi4py-openmpi findutils 
RUN echo 'module --ignore-cache load mpi/openmpi-x86_64' > /etc/profile.d/zz-openmpi.sh
RUN useradd -ms /bin/bash synergia
USER synergia
WORKDIR /home/synergia
RUN git clone http://cdcvs.fnal.gov/projects/contract-synergia2 synergia2-devel
WORKDIR /home/synergia/synergia2-devel
RUN git checkout -b devel origin/devel && ./bootstrap 
RUN . /etc/profile.d/modules.sh ; export MODULEPATH=/usr/share/modulefiles:$MODULEPATH ; module --ignore-cache load mpi/openmpi-x86_64 ; ./contract.py --configure openmpi_internal=0 || /bin/true
RUN . /etc/profile.d/modules.sh ; export MODULEPATH=/usr/share/modulefiles:$MODULEPATH ; module --ignore-cache load mpi/openmpi-x86_64 ; ./contract.py --configure mpi4py_internal=0 || /bin/true
RUN . /etc/profile.d/modules.sh ; export MODULEPATH=/usr/share/modulefiles:$MODULEPATH ; module avail
RUN . /etc/profile.d/modules.sh ; export MODULEPATH=/usr/share/modulefiles:$MODULEPATH ; module --ignore-cache load mpi/openmpi-x86_64 ; ./contract.py fftw3 || /bin/true
RUN . /etc/profile.d/modules.sh ; export MODULEPATH=/usr/share/modulefiles:$MODULEPATH ; module --ignore-cache load mpi/openmpi-x86_64 ; ./contract.py chef-libs || /bin/true
RUN . /etc/profile.d/modules.sh ; export MODULEPATH=/usr/share/modulefiles:$MODULEPATH ; module --ignore-cache load mpi/openmpi-x86_64 ; ./contract.py || /bin/true

