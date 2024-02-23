# Compiling SU2 on Local Linux

1. Install MPI package if it is not available in the system:

```
sudo apt update
sudo apt-get install libopenmpi-dev
```

2. Install conda/miniconda if it is not installed yet

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc
conda update conda
```

3. Set a conda environment

Find **environement.yml** file in the repo and download it. The path of the downloaded file is not important. Run the below commands to set the environment.

```
conda env create -f environment.yml
conda activate mpi4py
```

#4. Install mpi4py library
#
#```
#pip install --upgrade pip
#pip install mpi4py
#```

5. Clone a version of SU2. For the latest develop version:

```
git clone -b develop https://github.com/su2code/SU2.git <foldername_to_copy>
```

NOTE: If there is another SU2 folder built by meson and would like to be deleted, use: "rm -rf <su2_foldername>"

6. Descend into the SU2 directory:
   
```
cd <foldername>
```

7. Run meson to set build folder:

```
./meson.py build --prefix=$PWD -Denable-autodiff=true
```

NOTE: In this setup settings example, one additional flag *-Denable-autodiff=true* are set to activate adjoint optimization features of the code. For other flags and detailed info, see: https://su2code.github.io/docs_v7/Build-SU2-Linux-MacOS/


8. Export variables 

```
export SU2_RUN=<path_to_su2/bin>   eg: /home/be23361/Desktop/SU2/SU2/bin
export SU2_HOME=<path_to_su2>      eg: /home/be23361/Desktop/SU2/SU2
export PATH=$PATH:$SU2_RUN
export PYTHONPATH=$PYTHONPATH:$SU2_RUN
```

9. Install via ninja

```
./ninja -C build install
```

10. Test installation

```
mpiexec ./bin/SU2_CFD
```

This command should return an error such as **"The configuration file (.cfg) is missing!!"** and then MPI should abort. This is the expected behviour. Then a test case can be run with a config file.




   
