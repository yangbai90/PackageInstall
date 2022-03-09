# Installation of Lammps

## Step-0 Prerequirest
Before you start, it's better to have your GCC, openmpi or mpich installed. As we know, the MD simulation is time-consuming, therefore, I'd suggest installing the mpi version of Lammps. But, the sequential version (without mpi) also works fine for a small system.

## Step-1 Download
The download of vim can be done via:
```
git clone https://github.com/lammps/lammps.git
```
or go to the release page of [Lammps](https://github.com/lammps/lammps/tags)

## Step-2 configure and build
Firstly, you need to create the `build` folder:
```
cd lammps
mkdir build
cd build
```
Then, you can configure your lammps by using the following code:
```
cmake ../cmake \
../cmake/presets/all_on.cmake \
-DPKG_BODY=yes \
-DPKG_MANYBODY=yes \
-DPKG_INTERLAYER=yes \
-DPKG_CG-SDK=yes \
-DPKG_CLASS2=yes \
-DPKG_EFF=yes \
-DPKG_EXTRA-PAIR=yes \
-DPKG_FEP=yes \
-DPKG_MANIFOLD=yes \
-DPKG_MC=yes \
-DPKG_MGPT=yes \
-DPKG_MPIIO=yes \
-DPKG_OPT=yes \
-DPKG_ORIENT=yes \
-DPKG_PERI=yes \
-DPKG_REACTION=yes \
-DPKG_REAXFF=yes \
-DPKG_RIGID=yes \
-DPKG_SHOCK=yes \
-DPKG_TALLY=yes \
-DPKG_YAFF=yes \
-DBUILD_MPI=yes \
-DCMAKE_CXX_FLAGS="-O3 -march=native -fopenmp " \
-DCMAKE_C_FLAGS="-O3 -march=native -fopenmp " \
-DCMAKE_Fortran_FLAGS="-O3 -march=native -fopenmp " \
-DBUILD_TOOLS=yes \
-DCMAKE_INSTALL_PREFIX=/home/by/Programs/toolkits/gcc10/lammps
```
where `-DCMAKE_INSTALL_PREFIX=` should be changed to your own path.
Besides, more packages can be installed via:
```
-DPKG_I_want_xxx_package=yes
```
Afterwards, just run the `make` and `make install` to install your lammps:
```
make -j16
make install
```
next, you should add `lammps/bin/lmp` to your `.bashrc` file or other bash file to setup the enviroment.

It's done, and enjoy MD!
