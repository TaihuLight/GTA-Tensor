# GTA

Overview
---------------

**A General Framework for Tucker Factorization on Heterogeneous Platforms**  
[Sejoon Oh](https://www.sejoonoh.com/), [Namyong Park](http://namyongpark.com/), [Jungi Jang](https://datalab.snu.ac.kr/~jkjang/), [Lee Sael](https://leesael.github.io/), and [U Kang](https://datalab.snu.ac.kr/~ukang/)

[[Paper](https://datalab.snu.ac.kr/ptucker/ptucker.pdf)] [[Supplementary Material](https://datalab.snu.ac.kr/ptucker/supple.pdf)] (Submitted to TPDS Journal)

Usage
---------------

**GTA requires OpenMP (2.0+ version) and OpenCL (1.2+ version) libraries! (if you use gcc/g++ compiler, OpenMP is installed by default)**

"make" command will create a single executable file, which is "GTA".

The executable file takes five arguments, which are the path of input tensor file, path of directory for storing results, tensor rank, local size (64, 256, 512, and 1024 are recommended), number of GPUs, binary number indicating POTF (1) or FOTF (0). The arguments MUST BE valid and in the above order.

		ex) ./GTA input.txt result/ 10 256 1 1

If you put the command properly, GTA will write all values of factor matrices and a core tensor in the result directory set by an argument. (PLEASE MAKE SURE THAT YOU HAVE A WRITE PERMISSION TO THE RESULT DIRECTORY!).

		ex) result/FACTOR1, result/CORETENSOR

**We note that input tensors must follow base-1 indexing and outputs are based on base-0 indexing.**

Demo
---------------
To run the demo, please follow the following procedure. Sample tensor is created as 100x100x100 size with 1,000 observable entries.

	1. Type "make demo"
	2. Check "result" directory for the demo factorization results
  
Orthogonalization of Factor Matrices
---------------

You can apply QR decompositions to output factor matrices and core tensor according to the main paper using MATLAB or other languages. Notice that current version of P-Tucker does not orthogonalize factor matrices and update a core tensor.
