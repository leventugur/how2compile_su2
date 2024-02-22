# Compiling SU2 on Local Linux

1. Install MPI package if it is not available in the system:

```
sudo apt-get install libcr-dev
```

2. Install conda/miniconda if it is not installed yet

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc
conda update conda
```

4. Install mpi4py library

```
pip install --upgrade pip
pip install mpi4py
```

5. Clone a version of SU2. For the latest develop version:

```
git clone -b develop https://github.com/su2code/SU2.git <foldername_to_copy>
```

6. Descend into the SU2 directory:
   
```
cd <foldername>
```

7. Run meson to set build folder:

```
./meson.py build --prefix=$PWD -Denable-autodiff=true
```

NOTE: In this setup settings example, one additional flag *-Denable-autodiff=true* are set to activate adjoint optimization features of the code. For other flags and detailed info, see: https://su2code.github.io/docs_v7/Build-SU2-Linux-MacOS/


8. Install via ninja

```
./ninja -C build install
```

9. Test installation

```
mpiexec ./bin/SU2_CFD
```

This command should return an error such as **"The configuration file (.cfg) is missing!!"** and then MPI should abort. This is the expected behviour. Then a test case can be run with a config file.




   
