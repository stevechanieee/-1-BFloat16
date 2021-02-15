# BFloat16 #



## Hybridized On-Premise-Cloud Infrastructure ##

A key advantage of utilizing a cloud platform is that the requisite hardware resides in the cloud platform provider’s various data centers. Along this vein, scalability, elasticity, and other desired capabilities are inherently available. For certain testbed/experimentation platforms and even production environments, some hardware may remain on premise; this segment of the infrastructure that resides locally is considered on-premise-cloud infrastructure. An advantage of this paradigm is that the more frequently accessed datasets reside on the local network, although core services and other datasets may still be provisioned in the cloud. The three significant cloud outages of 2020 (https://techhq.com/2020/12/3-biggest-public-cloud-outages-of-2020/) provide enough pause so as to illuminate the interesting potentialities of a hybridized on-premise-cloud infrastructure.

## Advantage of Cloud Native Artificial Intelligence ##

As the cloud environment is, theoretically, available from anywhere with an Internet connection, it facilitates greater accessibility and collaboration. In addition, among other advantages, cloud environments are scalable for supporting greater volumes of data (i.e., cloud storage) and a potentially faster computing environment for processing greater volumes of data (i.e., cloud computing). In essence, the cloud offers an elastic environment. This is of great interest to Artificial Intelligence (AI) implementers, as the "cloud environment's contributions to AI's ascendancy go beyond just data," particularly as pertains to the two most common applications of AI: (1) Machine Learning (ML), and Deep Learning (DL).

*Source: https://www.ironmountain.com/resources/general-articles/c/cloud-computing-and-ai-have-combined-to-fuel-each-other-s-stunning-growth*

Typically, cloud platform providers natively support a variety of ML and DL frameworks as well as specific data types, via custom processors. For example, Amazon, Google, and other cloud platform providers have been steadily releasing custom processors, over the past several years, so as to improve the performance of their hyper-scale data center servers.

*Source: https://www.spglobal.com/marketintelligence/en/news-insights/latest-news-headlines/microsoft-designs-data-center-chip-to-compete-with-amazon-intel-8211-report-61823358*

On 1 December 2020, Amazon Web Services (AWS) debuted AWS Trainium (a custom processor for ML model training in the cloud). In 2017, Google announced its first-generation Tensor Processing Unit (TPU) (a custom processor for ML), and these were made available a year later in the cloud; on 29 July 2020, Google debuted its fourth-generation TPUs. 

*Source: https://aws.amazon.com/ec2/graviton/*<br/>
*Source: https://medium.com/sciforce/understanding-tensor-processing-units-10ff41f50e78*<br/>
*Source: https://venturebeat.com/2020/07/29/google-claims-its-new-tpus-are-2-7-times-faster-than-the-previous-generation/*

Overall, the custom processors of the various cloud platform providers are considered to be AI accelerator Application-Specific Integrated Circuits (ASICs). The cost of ASICs has decreased dramatically, as the prevalence of ASICs has grown amidst the "drive to create cutting-edge artificial-intelligence chips and cloud-computing services" by various technology companies (e.g., Facebook, Tesla).

*Source: https://www.electronicdesign.com/technologies/embedded-revolution/article/21808278/the-economics-of-asics-at-what-point-does-a-custom-soc-become-viable*

## Custom Processors in the Cloud ##

As previously discussed, to facilitate ML workloads (typically computationally intensive processes that might run for hours/days), Google's TPUs support a custom floating point format/data type entitled Brain Floating Point Format (BFloat16). BFloat 16 is designed to accelerate matrix multiplication operations.

By way of background information, the BFloat16 floating-point format for DL is an encoding format, which occupies 16 bits and represents a floating-point number. It is of the format [1:8:7], which has one sign bit, eight exponent bits, and seven mantissa bits (e.g., fraction field) plus one implicit mantissa bit. This differs from the IEEE Standard for Floating Point Arithmetic (IEEE 754) 16-bit floating point format (the IEEE 754 16-bit floating point format is assumed to have an implicit lead bit with value 1 unless the exponent field is stored with all zeros; hence, although there are only 10 bits of significand, there are 11 bits of significand precision), which was not designed for DL. The floating-point format is comprised of three binary fields: +/- mantissa * 2^exponent (i.e., the sign bit field of +/-, the exponent field of ^exponent, and the fraction field of mantissa).

In essence, Bfloat16 follows the same format as a standard IEEE 754 single-precision 32-bit floating-point format, but truncates the mantissa field from 23 bits to just 7 bits. Preserving the exponent bits keeps the format to the same range as the 32-bit single-precision floating-point (~1e-38 to ~3e38).

Source: https://en.wikichip.org/wiki/brain_floating-point_format

## Cloud Platform Instance ##

For an involved cloud instance (i.e., a virtual machine running a workload in a cloud computing environment), various drivers, toolkits, and runtime are needed for the involved cloud computing environment. This might include, by way of example, the following: (1) NVIDIA driver, (2) Compute Unified Device Architecture (CUDA) toolkit, and (3) CUDA runtime.

*Source: https://cloud.google.com/compute/docs/gpus/install-drivers-gpu*

In general, increasing the size of the involved neural network results in enhanced accuracy. However, as the neural network grows, the memory and computational requirements also grow. Being in the cloud, scalability is readily accommodated. 

*Source: https://arxiv.org/abs/1710.03740*

## Graphics Processing Unit Programming Framework ##

CUDA and OpenCL are both Graphics Processing Unit (GPU) programming frameworks, which leverage the use of GPUs and their custom processors. Whereas CUDA is proprietary to NVIDIA, OpenCL is an open standard maintained by the Khronos Group consortium, whose members are listed here: https://www.khronos.org/members/list. 

Depending on the GPU type, there are particular NVIDIA driver versions required as well as minimum recommended CUDA Toolkit versions, such as shown in Table 1 below.

**Table 1: GPU Type, Required NVIDIA Driver Version, and Minimum Recommended CUDA Toolkit Version**

| GPU Type    | GPU Description | Minimum Required NVIDIA Driver Version | NVIDIA Driver Version Release Date | Minimum Recommended CUDA Software Development Kit/Toolkit Version |
|-------------|-----------------|-----------------------|------------------------------------|------------------------------------------|
| NVIDIA A100 | Tensor Core GPU | **Linux: 450.80.02**      | 9/30/20                            | Linux: CUDA Toolkit 11.1                 |
| All other   | e.g., TPU       | **Linux : NVIDIA 410.79** | 2/27/20                            | Linux: CUDA Toolkit 11.1             |
| NVIDIA T4   | Tensor Core GPU | Linux: 410.79         | 12/3/18                            | Linux: CUDA Toolkit 10.1 update2         |

*Source: https://cloud.google.com/compute/docs/gpus/install-drivers-gpu*

The CUDA Software Development Kit (SDK) v11.0 – v11.2 supports the delineated BFloat16 data type. A principal benefit of BFloat16 is to reduce the storage requirements and increase the computational speed of DL algorithms. NVIDIA GPU-Accelerated Server Platforms, running CUDA SDK v11.0+, whether on-premise (a.k.a. on-prem) or in the cloud, can leverage BFloat16; BFloat16 is an excellent alternative to the IEEE 754 16-bit Floating Point (FP16) format, for although it has reduced precision, it has the numerical range of FP32.

## GNU Octave ##

The chosen platform for the experimentation herein has been the GNU Octave platform. As a numerical computation platform, it is mostly compatible with comparable platforms, such as MATLAB; however, as GNU Octave is released under a GNU GPLv3 license, the source code was modified for the experiments conducted herein, which resulted in a Modified GNU Octave (M-GNU-O) platform that can better leverage certain accelerants. In addition to GNU Octave, Julia was utilized as well.

## Julia ##

Among other high-performance programming languages (e.g., GNU Octave, Go, NumPy, etc.), Julia is a high-level, high-performance programming language, which was designed for numerical analysis and computational science.

JuliaMath (i.e., mathematics made easy in Julia) defines the BFloat16 data type. 

*Source: https://github.com/JuliaMath/BFloat16s.jl*

JuliaGPU "is a Github organization created to unify the many packages for programming GPUs in Julia;" JuliaGPU is also described as a "high-performance GPU programming in a high-level language."

*Source: https://juliagpu.org*

According to JuliaGPU.org (https://juliagpu.org), "the best supported GPU platform in Julia is NVIDIA CUDA."

## CUDA Progamming in Julia (CUDA.jl) ##

The Julia version release history is available here:
https://github.com/JuliaLang/julia/releases

For convenience, Julia version information is provided in Table 2 below.

**Table 2: Julia Release Version Information**

| Julia Release Version Number | Release Date |
|----------------------|--------------|
| v1.4.1               | 4/14/20      |
| v1.4.2               | 5/23/20      |
| v1.5.0-beta1         | 5/28/20      |
| v1.5.0-rc1           | 6/26/20      |
| v1.5.0-rc2           | 7/27/20      |
| v1.5.0               | 8/1/20       |
| v1.5.1               | 8/25/20      |
| v1.5.2               | 9/24/20      |
| v1.5.3               | 11/9/20      |
| **v1.6.0-beta**          | 1/8/21       |

As can be seen, the most current version is Julia v1.6.0.

The most recent version of CUDA.jl requires Julia v1.6.0 (or higher).

From Julia, add the CUDA.jl Pkg, via the Pkg API:


```javascript
julia> import Pkg; Pkg.add("CUDA")
```

Precompile the Pkg and download the apropos CUDA toolkit:

```javascript
julia> using CUDA
```

```javascript
julia> CUDA.versioninfo()
```

Query to confirm the involved device's compute capability:

```javascript
julia> [CUDA.capability(dev) for dev in CUDA.devices()]
1-element Vector{VersionNumber}:
 v"8.6"
```

The most recent version of CUDA.jl requires a CUDA compute capability version of 5.0 (or higher).

An interim summary of the CUDA compute capability versions (ranging from 1.0 through 8.6) are shown in Table 3 below:

**Table 3: CUDA Compute Capability and Microarchitecture Information**
| Version Number | Microarchitecture Name |
| --- | --- |
| 1.0 | Tesla |
| 1.1 | Tesla |
| 1.2 | Tesla |
| 1.3 | Tesla |
| 2.0 | Fermi |
| 2.1 | Fermi |
| 3.0 | Kepler |
| 3.2 | Kepler |
| 3.5 | Kepler |
| 3.7 | Kepler |
| 5.0 | Maxwell |
| 5.2 | Maxwell |
| 5.3 | Maxwell |
| 6.0 | Pascal |
| 6.1 | Pascal |
| 6.2 | Pascal |
| 7.0 | Volta |
| 7.2 | Volta |
| 7.5 | Turing |
| 8.0 | Ampere |
| **8.6** | Ampere |

An interim summary of the version information for the various components, as the constituent components in the toolkit are versioned independently as of CUDA v11, are shown in Table 4 below:

**Table 4: CUDA 11 Component Version Information**
| Component Name | Version Number | Supported Architectures |
| --- | --- | --- |
| CUDA Runtime (cudart) | 11.0.221 | x86_64, POWER, Arm64 |
| cuobjdump | 11.0.221 | x86_64, POWER, Arm64 |
| CUPTI | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA Demo Suite | 11.0.167 | x86_64 |
| CUDA GDB | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA Memcheck | 11.0.221 | x86_64, POWER |
| CUDA NVCC | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA nvdisasm | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA NVML Headers | 11.0.167 | x86_64, POWER, Arm64 |
| CUDA nvprof | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA nvprune | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA NVRTC | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA NVTX | 11.0.167 | x86_64, POWER, Arm64 |
| CUDA NVVP | 11.0.221 | x86_64, POWER |
| CUDA Samples | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA Compute Sanitizer API | 11.0.221 | x86_64, POWER, Arm64 |
| CUDA cuBLAS | 11.2.0.252 | x86_64, POWER, Arm64 |
| CUDA cuFFT | 10.2.1.245 | x86_64, POWER, Arm64 |
| CUDA cuRAND | 10.2.1.245 | x86_64, POWER, Arm64 |
| CUDA cuSOLVER | 10.6.0.245 | x86_64, POWER, Arm64 |
| CUDA cuSPARSE | 11.1.1.245 | x86_64, POWER, Arm64 |
| CUDA NPP | 11.1.0.245 | x86_64, POWER, Arm64 |
| CUDA nvJPEG | 11.1.1.245 | x86_64, POWER, Arm64 |
| Nsight Eclipse Plugins | 11.0.221 | x86_64, POWER |
| Nsight Compute | 2020.1.2.4 | x86_64, POWER, Arm64 |
| Nsight Windows NVTX | 1.21018621 | x86_64, POWER, Arm64 |
| Nsight Systems | 2020.3.2.6 | x86_64, POWER, Arm64 |
| Nsight Visual Studio Edition (VSE) | 2020.1.2.20203 | x86_64 (Windows) |
| NVIDIA Linux Driver | 450.51.06 | x86_64, POWER, Arm64 |
| NVIDIA Windows Driver | 451.82 | x86_64 (Windows) |
Source: https://docs.nvidia.com/cuda/archive/11.0/cuda-toolkit-release-notes/

<br/>
<br/>

With regards to dependencies, please note the deprecations at CUDA v11:

1. cusparse<t>gemmi() <br/>
2. cusparseXaxpyi -> cusparseAxpby() <br/>
3. cusparseXgthr -> cusparseGather()<br/>
4. cusparseXgthrz -> cusparseGather()<br/>
5. cusparseXroti -> cusparseRot()<br/>
6. cusparseXsctr -> cusparseScatter()<br/>
	
For the functions involved, such as for (1) through (6) above, please search for: "This function performs the following matrix-matrix operations" or the replacement functions (as shown above) on this page: https://docs.nvidia.com/cuda/cusparse/index.html.

Overall, the dropped features include: 
* cusparse<t>gemmi()<br/>
* cusparseXaxpyi, cusparseXgthr, cusparseXgthrz, cusparseXroti, cusparseXsctr<br/>
* Hybrid format enums and helper functions: cusparseHybPartition_t, cusparseHybPartition_t, cusparseCreateHybMat, cusparseDestroyHybMat<br/>
* Triangular solver enums and helper functions: cusparseSolveAnalysisInfo_t, cusparseCreateSolveAnalysisInfo, cusparseDestroySolveAnalysisInfo<br/>
* Sparse dot product: cusparseXdoti, cusparseXdotci<br/>
* Sparse matrix-vector multiplication: cusparseXcsrmv, cusparseXcsrmv_mp<br/>
* Sparse matrix-matrix multiplication: cusparseXcsrmm, cusparseXcsrmm2<br/>
* Sparse triangular-single vector solver: cusparseXcsrsv_analysis, cusparseCsrsv_analysisEx, cusparseXcsrsv_solve, cusparseCsrsv_solveEx<br/>
* Sparse triangular-multiple vectors solver: cusparseXcsrsm_analysis, cusparseXcsrsm_solve<br/>
* Sparse hybrid format solver: cusparseXhybsv_analysis, cusparseShybsv_solve<br/>
* Extra functions: cusparseXcsrgeamNnz, cusparseScsrgeam, cusparseXcsrgemmNnz, cusparseXcsrgemm<br/>
* Incomplete Cholesky Factorization, level 0: cusparseXcsric0<br/>
* Incomplete LU Factorization, level 0: cusparseXcsrilu0, cusparseCsrilu0Ex<br/>
* Tridiagonal Solver: cusparseXgtsv, cusparseXgtsv_nopivot<br/>
* Batched Tridiagonal Solver: cusparseXgtsvStridedBatch<br/>
* Reordering: cusparseXcsc2hyb, cusparseXcsr2hyb, cusparseXdense2hyb, cusparseXhyb2csc, cusparseXhyb2csr, cusparseXhyb2dense<br/>

*Source: https://docs.nvidia.com/cuda/archive/11.0/cuda-toolkit-release-notes/#deprecated-features*

The cusparse (a.k.a. cuSPARSE) library contains basic linear algebra subroutines (i.e., a set of instructions designed to perform a frequently utilized operation), which are geared for handling sparse matrices, particularly those sparse matrices, whose number of zero elements represent > 95% of the total entries.

*Source: https://docs.nvidia.com/cuda/cusparse/index.html*

The cuSPARSE library subroutines can be classified into four categories:
1. operations between a vector in sparse format and a vector in dense format;<br/>
2. operations between a matrix in sparse format and a vector in dense format;<br/>
3. operations between a matrix in sparse format and a set of vectors in dense format (which can also usually be viewed as a dense tall matrix);<br/>
4. operations that allow conversion between different matrix formats, and compression of Compressed Sparse Row (CSR) matrices.<br/>

*Source:https://docs.nvidia.com/cuda/cusparse/index.html*

In numerical analysis and scientific computing, a sparse matrix (a.k.a. sparse array) is a matrix, wherein most of the elements are zero. There is no strict definition regarding how many elements are zero for a matrix to be considered sparse. However, one of the more universally acknowledged criterion asserts, "the number of non-zero elements is roughly the number of rows or columns." In contrast, if the majority of the elements are non-zero, then the matrix is considered dense. The sparsity of the matrix = count for the zero elements / count for the total elements.

The following are exemplars of efficient structures for constructing sparse matrices:
* Dictionary of keys (DOK)-based sparse matrix: the array is represented as a dictionary that maps pairs (row, column) to the value of the elements.
* List of Lists (LIL)-based sparse matrix: the array is represented as a list of rows, and each row is represented as list of pairs (index position, value).
* Coordinate list (COO)-based sparse matrix: the array is represented as a list of tuples (row, column, value).
* Compressed Sparse Column (CSC) or Compressed Column Storage (CCS) (a.k.a. Harwell-Boeing sparse matrix format): specified by the arrays {val, row_ind, col_ptr}, where val stores the non-zero elements of the matrix (i.e., the floating-point numbers), row_ind stores the row indices of each nonzero element, and col_ptr stores the index of the elements in val which start a column of matrix A.
* Compressed Sparse Row (CSR) or Compressed Row Storage (CRS)(a.k.a. Yale sparse matrix format): specified by the arrays {val, col_ind, row_ptr}, where val stores the non-zero elements of the matrix (i.e., the floating-point numbers), col_ind stores the column indices of each nonzero element, and row_ptr stores the index of the elements in val which start a column of matrix A.

It should be axiomatic that operations involving standard dense matrix structures expend a great deal of processing and storage for the zeros. Sparse matrix structures are, theoretically, more easily compressed and, therefore, require significantly less processing and storage. 

Depending upon the permissibility of rounding, the following data types may be used:
float: a single precision 32-bit IEEE 754 floating point format. 
double: a double precision 64-bit IEEE 754 floating point format. 
decimal: will 100% accurately represent any number, whereas float and double are not able to accurately represent all numbers.

Other data types, which are available from the CUDA library, include:
cuComplex: creates a new complex single precision number consisting of the given real and imaginary part. 
cuDoubleComplex: creates a new complex double precision number consisting of the given real and imaginary part. 

Further CUDA library information can be found here: https://docs.nvidia.com/cuda-libraries/index.html

An interim summary of the CUDA toolkit versions (ranging from 1.0 through 11.2.0) are shown in Table 5 below:

**Table 5: CUDA Toolkit Version Information**
|     |     |
| --- | --- |
| Toolkit Version Number | Release Date |
| **11.2.0** | Dec 2020 |
| 11.1.1 | Oct 2020 |
| 11.1.0 | Sept 2020 |
| 11.0 Update 1 | Aug 2020 |
| 11.0 | May 2020 |
| 10.2 | Nov 2019 |
| 10.1 Update 2 | Aug 2019 |
| 10.1 Update 1 | May 2019 |
| 10.1 | Feb 2019 |
| 10.0 | Sept 2018 |
| 9.2 | May 2018 |
| 9.1 | Dec 2017 |
| 9.0 | Sept 2017 |
| 8.0 GA 2 | Feb 2017 |
| 8.0 GA 1 | Sept 2016 |
| 7.5 | Sept 2015 |
| 7.0 | March 2015 |
| 6.5 | August 2014 |
| 6.0 | April 2014 |
| 5.5 | July 2013 |
| 5.0 | Oct 2012 |
| 4.2 | April 2012 |
| 4.1 | Jan 2012 |
| 4.0 | May 2011 |
| 3.2 | Nov 2010 |
| 3.1 | June 2010 |
| 3.0 | March 2010 |
| Open Computing Language (OpenCL) Release 1.0 | Sept 2009 |
| 2.3 | June 2009 |
| 2.2 | May 2009 |
| 2.1 | Jan 2009 |
| 2.0 | Aug 2008 |
| 1.1 | Dec 2007 |
| 1.0 | June 2007 |

*Source: https://developer.nvidia.com/cuda-toolkit-archive*<br/>
*Source: https://docs.nvidia.com/cuda/archive/11.0/cuda-toolkit-release-notes/*

### Interim Findings ###

As of this commit, to utilize the BFloat16 data type:<br/>
* CUDA Software Development Kit (SDK) v11.0 (or higher) must be utilized; the most current CUDA SDK is v11.2.<br/>
* The most recent version of CUDA.jl requires Julia v1.6.0 (or higher).<br/>
* The most recent version of CUDA.jl requires a CUDA compute capability version of 5.0 (or higher); the most current CUDA compute capability is v8.6.
* The on-prem component, will likely require 450.80.02 drivers; the cloud component will likely require 410.79 (for initial testing purposes).








