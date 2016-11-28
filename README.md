Experimental SoftBoundCETS for LLVM-3.9 
=======================================

This is an experimental version of SoftBoundCETS for LLVM-3.9. It is
not yet ready for any serious use.

For more technical details and algorithms, visit SoftBoundCETS website
at http://www.cs.rutgers.edu/~santosh.nagarakatte/softbound/

Using SoftBoundCETS for LLVM/Clang-3.9 on a x86-64 machine with Linux OS
========================================================================


1. Download the github repository from https://github.com/santoshn/SoftBoundCETS-3.9.git

2. Build SoftBoundCETS-3.9

   1. Goto to directory SoftBoundCETS-3.9 by executing the following command

            cd SoftBoundCETS-3.9
	    mkdir build
	    cd build

   2. Configure LLVM, clang and softboundcets with the following command

            cmake ../llvm-3.9/
	    make -j8

3. Set up your environment to use SoftBoundCETS

   For example in bash, it would be

         export PATH=<git_repo>/SoftBoundCETS-3.9/build/bin:$PATH

4. Compile the SoftBoundCETS runtime library

         cd <git_repo>
         cd runtime
         make

5. Test whether it all worked

   1. Compile

            cd tests
            clang -fsoftboundcets test.c -o test -L<git_repo>/runtime -lm -lrt -lsoftboundcets_rt

2. Run the test program

            ./test

      Enter 10; the program executes successfully.

      Enter 105; a memory safety violation is triggered.


NOTES and TODO
==============

(1) LTO is still not enabled. 

(2) Checks are not currently inlined.

(3) Enable spatial and temporal check elimination

(4) Add separate modes for softbound, cets, and softboundcets
