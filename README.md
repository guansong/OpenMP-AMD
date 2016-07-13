# OpenMP-AMD

A repo manifest

This includes the source code to build a prototype supporting OpenMP in LLVM/Clang on an AMD Linux system.

Supposing you have a github account, on an AMD ROCM platform, you can do

mkdir workspace; cd workspace; repo init -u https://github.com/guansong/OpenMP-AMD.git; repo sync

to get the whole project source in the workspace directory

Set the lightening compiler path first. By default /opt/amd/llvm/bin will be used.

  export CLANG_OCL_PATH=/path/to/lightening_compiler/bin

mkdir build; cd build; cmake ...

Configure and build the clang as you usually do, this will also use the lightenling compiler selected above to build the AMD device runtime for OpenMP.

Set up the envrionment through these steps as required by clang,

  export PATH=`pwd`/bin:$PATH
  
  export C_INCLUDE_PATH=`pwd`/projects/openmp/runtime/src:$C_INCLUDE_PATH
  
  export CPLUS_INCLUDE_PATH=`pwd`/projects/openmp/runtime/src:$CPLUS_INCLUDE_PATH
  
  export LIBRARY_PATH=`pwd`/lib:$LIBRARY_PATH
  
  export LD_LIBRARY_PATH=`pwd`/lib:$LD_LIBRARY_PATH

Go back to the workspace dir,

  cp llvm/projects/openmp/libomptarget/test/offloading/offloading_success.c .

Compile the example,

  clang  -fopenmp -omptargets=hsail64 -lelf -lffi -lhsa-runtime64 offloading_success.c

or

  env MCPU=carrizo clang  -v -save-temps -fopenmp -omptargets=hsail64 -lelf -lffi -lhsa-runtime64 offloading_success.c

And run the executable a.out


