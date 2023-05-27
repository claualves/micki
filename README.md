### micki

A modular, extensible, robust object-oriented microkinetic modeling package
written in Python.

### DEPENDENCIES:
 * lapack (MKL by default "-lmkl_rt"; can specify alternative LAPACK library via MICKI_LAPACK environmental variable)
 * ase
 * numpy
 * sympy
 * sundials (C library) - Tested with version 4.0. Compile Sundials with the following flags to cmake: -DFCMIX_ENABLE=ON -DCMAKE_C_FLAGS="-fPIC" -DLAPACK_ENABLE=ON -DSUNDIALS_INDEX_SIZE=32

### Detailed installation instructions:
#install ASE (which includes numpy as a dependancy) and sympy
pip3 install --user ase
pip3 install --user sympy

#install sundials
wget https://github.com/LLNL/sundials/releases/download/v4.0.2/sundials-4.0.2.tar.gz
tar zxvf sundials-4.0.2.tar.gz
cd sundials-4.0.2
mkdir build
cd build
#ensure that MKL is found!
. /opt/intel/mkl/bin/mklvars.sh intel64
cmake .. -DFCMIX_ENABLE=ON -DCMAKE_C_FLAGS="-fPIC" -DLAPACK_ENABLE=ON -DSUNDIALS_INDEX_SIZE=32 -DCMAKE_INSTALL_PREFIX=~/sundials
#make sure MKL BLAS/LAPACK were found!
make
make install

git clone https://github.com/jrschmidt2/micki.git 
