# OpenMP-AMD

A repo manifest

This includes the source code to build a prototype supporting OpenMP in LLVM/Clang on an AMD Linux system.

Supposing you have a github account, on an AMD ROCM platform, you can do

mkdir workspace; cd workspace; repo init -u git@github.com:guansong/OpenMP-AMD.git; repo sync

to get the whole project source in the workspace directory

mkdir build; cd build; cmake ...

Configure and build the clang as you usually do, it will include the OpenMP runtime. 

After building everything, you can set up the envrionment

  export PATH=`pwd`/bin:$PATH
  export C_INCLUDE_PATH=`pwd`/projects/openmp/runtime/src:$C_INCLUDE_PATH
  export CPLUS_INCLUDE_PATH=`pwd`/projects/openmp/runtime/src:$CPLUS_INCLUDE_PATH
  export LIBRARY_PATH=`pwd`/lib:$LIBRARY_PATH
  export LD_LIBRARY_PATH=`pwd`/lib:$LD_LIBRARY_PATH

Go back to the workspace dir,

  cp the example


