# OpenMP-AMD

A repo manifest

This is to build LLVM/clang OpenMP on AMD system for Linux

Suppose you have a github account, you can do

mkdir workspace; cd workspace; repo init -u git@github.com:guansong/OpenMP-AMD.git; repo sync

to get the whole project source in the workspace directory

configure and build

setting up

  export PATH=`pwd`/bin:$PATH
  export C_INCLUDE_PATH=`pwd`/projects/openmp/runtime/src:$C_INCLUDE_PATH
  export CPLUS_INCLUDE_PATH=`pwd`/projects/openmp/runtime/src:$CPLUS_INCLUDE_PATH
  export LIBRARY_PATH=`pwd`/lib:$LIBRARY_PATH
  export LD_LIBRARY_PATH=`pwd`/lib:$LD_LIBRARY_PATH
