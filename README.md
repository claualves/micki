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
#install ASE (which includes numpy as a dependancy) and sympy<br>
pip3 install --user ase<br>
pip3 install --user sympy<br>

#install sundials<br>
wget https://github.com/LLNL/sundials/releases/download/v4.0.2/sundials-4.0.2.tar.gz<br>
tar zxvf sundials-4.0.2.tar.gz<br>
cd sundials-4.0.2<br>
mkdir build<br>
cd build<br>
#ensure that MKL is found!<br>
. /opt/intel/mkl/bin/mklvars.sh intel64<br>
cmake .. -DFCMIX_ENABLE=ON -DCMAKE_C_FLAGS="-fPIC" -DLAPACK_ENABLE=ON -DSUNDIALS_INDEX_SIZE=32 -DCMAKE_INSTALL_PREFIX=~/sundials<br>
#make sure MKL BLAS/LAPACK were found!<br>
make<br>
make install<br>

#fetch Micki itself<br>
git clone https://github.com/jrschmidt2/micki.git
