# Submodules CMake Tutorial

**NOTES**: 
- This page is intended for personal use
- It is based on Windows OS

## Requirement

- [IPOPT](https://coin-or.github.io/Ipopt/)
- [MUMPS](https://mumps-solver.org/index.php)
- [MSYS2](https://www.msys2.org/) to use MinGW

## Setup the requirement

1. Download and install the MSYS2 installer from [here](https://www.msys2.org/)
2. Open "MSYS2 MINGW2" application from start menu
3. Update the MSYS2 using the following command  
    `$ pacman -Syuu`
4. Install gcc, make, and cmake in MSYS2. Since mingw64 environment of MSYS2 is recommended to use when using CMake, so we install specific mingw version of all the package. For searching a package, you can use the following  
    > $ pacman -Ss gcc  

    > $ pacman -Ss make

    > $ pacman -Ss cmake

    to install specific mingw64 version, use the following

    > $ pacman -S mingw-w64-x86_64-gcc

    > $ pacman -S mingw-w64-x86_64-make

    > $ pacman -S mingw-w64-x86_64-cmake

5. 