# OpenMP-AMD

A repo manifest

This includes the source code to build a prototype supporting OpenMP 4.x with offloading feature in LLVM/Clang on an AMD Linux system.

On an AMD ROCM platform, you can do

mkdir workspace; cd workspace; repo init -u https://github.com/guansong/OpenMP-AMD.git; repo sync

to get the whole project source in the workspace directory

Set the lightening compiler path first. By default /opt/amd/llvm/bin will be used.

  export CLANG_OCL_PATH=/path/to/lightening_compiler/bin

mkdir build; cd build; cmake ...

Configure and build the clang as you usually do, this will also use the lightenling compiler selected above to build the AMD device runtime for OpenMP.

Set up the envrionment variables required by clang, such as bin, include and library paths. If using bash, you can simply stay in the build dir, and do

  source ../.repo/manifests/setup/setenv

Go back to the workspace dir, and copy an example

  cd -; cp llvm/projects/openmp/libomptarget/test/offloading/offloading_success.c .

Compile

  clang -v -fopenmp -omptargets=hsail64 -lelf -lffi -lhsa-runtime64 offloading_success.c

or

  env MCPU=fiji clang -v -save-temps -fopenmp -omptargets=hsail64 -lelf -lffi -lhsa-runtime64 offloading_success.c

Run the a.out


