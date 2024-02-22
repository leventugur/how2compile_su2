# Compiling SU2 on ARCHER2

1. Clone a version of SU2. For the latest develop version:

```
git clone -b develop https://github.com/su2code/SU2.git <foldername_to_copy>
```

2. Descend into the SU2 directory:
   
```
cd <foldername>
```

3. Set C compiler variables:

```
export CC=cc 
export CXX=CC 
export MPICC=cc
export MPICXX=CC
```

4. Run meson to set build folder:

```
./meson.py build --prefix=$PWD -Dcustom-mpi=true -Denable-autodiff=true
```

NOTE: In this setup settings example, two additional flags *-Dcustom-mpi=true* and *-Denable-autodiff=true* are set to activate parallel computing and adjoint optimization features of the code. For other flags and detailed info, see: https://su2code.github.io/docs_v7/Build-SU2-Linux-MacOS/


5. Install via ninja

```
 ./ninja -C build install
```



   
