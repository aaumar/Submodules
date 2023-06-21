# Submodules CMake Tutorial

**NOTES**: 
- This page is intended for personal use.
- It is based on Windows OS.
- The goal is to use CppAD as submodule of the project.

## Requirement

- [IPOPT](https://coin-or.github.io/Ipopt/)
- [MUMPS](https://mumps-solver.org/index.php)
- [MSYS2](https://www.msys2.org/) to use MinGW

## Setup the requirement

1. Download and install the MSYS2 installer from [here](https://www.msys2.org/)
2. Open "MSYS2 MINGW2" application from start menu
3. Update the MSYS2 using the following command  
`$ pacman -Syuu`
4. Install gcc, make, and cmake in MSYS2. Since mingw64 environment of MSYS2 is recommended to use when using CMake, so we install specific mingw version of all the package. For searching a package, you can use the following command
```
pacman -Ss gcc
pacman -Ss cmake
```
to install specific mingw64 version, use the following  
```
pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gcc-fortran
pacman -S mingw-w64-x86_64-cmake mingw-w64-x86_64-make
```
5. Install packages required for ipopt  
```
pacman -S binutils diffutils git grep patch pkg-config mingw-w64-x86_64-lapack mingw-w64-x86_64-metis
```
6. Install MUMPS Linear Solver  
```
git clone https://github.com/coin-or-tools/ThirdParty-Mumps.git
cd ThirdParty-Mumps
./get.Mumps
./configure
make -j4
make install
```
7. Install IPOPT  
```
git clone https://github.com/coin-or/Ipopt.git
cd Ipopt
mkdir build
cd build
../configure
make -j4
make test
make install
```
8. Add `C:\msys64\mingw64\bin` to PATH (assuming that you install MSYS2 into `C:msys64\`)

## Building the package

1. In VSCode, open terminal by `ctrl + shift + P` --> `View: Toogle Terminal`
2. Open this repository folder in your VSCode
3. The terminal in VSCode will be opened. All installation from mingw can be used in VSCode terminal after adding mingw to the path (step #8)
4. add cppad as submodule into `external/cppad`  
`git submodule add https://github.com/coin-or/CppAD.git external/cppad`
5. cmake the repository (try to use Ninja instead of MinGW MakeFiles for faster compilation time)  
`cmake -Dinclude_ipopt=TRUE -S . -B build -G "Ninja"`  
explanation:  
    - `-Dinclude_ipopt=TRUE`: include IPOPT in CppAD packages
    - `-G "Ninja"`: Specify Ninja as generator  

6. After generating makefile using the above command, you can build and run from VSCode directly. 
    - Click play button on the bottom of your VSCode to build and run your program. 
    - Edit and save your CMakeLists.txt to update your current build.

## To-do Lists
- [ ] Auto download submodule when running cmake