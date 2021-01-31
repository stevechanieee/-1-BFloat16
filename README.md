

A key advantage of utilizing a cloud platform is that the requisite hardware resides in the provider’s data centers. Along this vein, scalability, elasticity, and other desired capabilities are available. For certain testbed/experimentation platforms, some hardware may remain on premise; this segment of the infrastructure that resides locally is considered on-premise-cloud infrastructure. A key advantage is that the more frequently accessed datasets reside on the local network, although core services and other datasets are still provisioned in the cloud. Moreover, three significant cloud outages in 2020 (https://techhq.com/2020/12/3-biggest-public-cloud-outages-of-2020/) provide enough pause so as to illuminate the interesting potentialities of a hybridized on-premise-cloud infrastructure.



According to Juliagpu.org (https://juliagpu.org), "the best supported GPU platform in Julia is NVIDIA CUDA."


#CUDA Progamming in Julia (CUDA.jl)#

The Julia version release history is available here:
https://github.com/JuliaLang/julia/releases

The most recent version is Julia v1.6.0.

The most recent version of CUDA.jl requires Julia v1.6.0 (or higher).

Add the CUDA.jl Pkg, via the Pkg API:


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

The most recent version of CUDA.jl also required a compute capability version of 5.0 (or higher).

An interim summary of the compute capability versions (ranging from 1.0 through 8.6) are shown in Table 1 below:

**Table 1: CUDA Compute Capability and Microarchitecture Information**
<table>
<thead class="thead" align="left">
<tr class="row">
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Version Number</th>
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Microarchitecture Name</th>
</tr>
</thead>
	<tbody>
		<tr>
			<td>1.0</td>
			<td rowspan="4">Tesla</td>
		</tr>
		<tr>
			<td>1.1</td>
		</tr>
		<tr>
			<td>1.2</td>
		</tr>
		<tr>
			<td>1.3</td>
		</tr>
		<tr>
			<td>2.0</td>
			<td rowspan="2">Fermi</td>
		</tr>
		<tr>
			<td>2.1</td>
		</tr>
		<tr>
			<td>3.0</td>
			<td rowspan="4">Kepler</td>
		</tr>
		<tr>
			<td>3.2</td>
		</tr>
		<tr>
			<td>3.5</td>
		</tr>
		<tr>
			<td>3.7</td>
		</tr>
		<tr>
			<td>5.0</td>
			<td rowspan="3">Maxwell</td>
		</tr>
		<tr>
			<td>5.2</td>
		</tr>
		<tr>
			<td>5.3</td>
		</tr>
		<tr>
			<td>6.0</td>
			<td rowspan="3">Pascal</td>
		</tr>
		<tr>
			<td>6.1</td>
		</tr>
		<tr>
			<td>6.2</td>
		</tr>
		<tr>
			<td>7.0</td>
			<td rowspan="2">Volta</td>
		</tr>
		<tr>
			<td>7.2</td>
		</tr>
		<tr>
			<td>7.5</td>
			<td>Turing</td>
		</tr>
		<tr>
			<td>8.0</td>
			<td rowspan="2">Ampere</td>
		</tr>
		<tr>
			<td>8.6</td>
		</tr>
	</tbody>
</table>

 
An interim summary of the version information for the various components, as the constituent components in the toolkit are versioned independently as of CUDA v11, are shown in Table 2 below:

**Table 2: CUDA 11 Component Version Information**
<table>
<thead class="thead" align="left">
<tr class="row">
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Component Name</th>
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Version Number</th>
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Supported Architectures</th>
</tr>
</thead>
<tbody class="tbody">
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA Runtime (cudart)</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">cuobjdump</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUPTI</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA Demo Suite</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.167</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA GDB</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA Memcheck</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA NVCC</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA nvdisasm</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA NVML Headers</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.167</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA nvprof</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA nvprune</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA NVRTC</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA NVTX</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.167</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA NVVP</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA Samples</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA Compute Sanitizer API</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA cuBLAS</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.2.0.252</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA cuFFT</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">10.2.1.245</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA cuRAND</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">10.2.1.245</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA cuSOLVER</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">10.6.0.245</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA cuSPARSE</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.1.1.245</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA NPP</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.1.0.245</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">CUDA nvJPEG</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.1.1.245</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">Nsight Eclipse Plugins</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">Nsight Compute</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">2020.1.2.4</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">Nsight Windows NVTX</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">1.21018621</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">Nsight Systems</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">2020.3.2.6</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">Nsight Visual Studio Edition (VSE)</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">2020.1.2.20203</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64 (Windows)</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">NVIDIA Linux Driver</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">450.51.06</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top"  rowspan="1" colspan="1">NVIDIA Windows Driver</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">451.82</td>
<td class="entry" valign="top"  rowspan="1" colspan="1">x86_64 (Windows)</td>
</tr>
</tbody>
</table>
Source: https://docs.nvidia.com/cuda/archive/11.0/cuda-toolkit-release-notes/

<br/>
<br/>

With regards to dependencies, please note the deprecations at v11:

1. cusparse<t>gemmi()
2. cusparseXaxpyi -> cusparseAxpby() 
3. cusparseXgthr -> cusparseGather()
4. cusparseXgthrz -> cusparseGather()
5. cusparseXroti -> cusparseRot()
6. cusparseXsctr -> cusparseScatter()



The cuSPARSE library contains a set of basic linear algebra subroutines used for handling sparse matrices. The library targets matrices with a number of (structural) zero elements which represent > 95% of the total entries.

The library routines can be classified into four categories:

Level 1: operations between a vector in sparse format and a vector in dense format
Level 2: operations between a matrix in sparse format and a vector in dense format
Level 3: operations between a matrix in sparse format and a set of vectors in dense format (which can also usually be viewed as a dense tall matrix)
Conversion: operations that allow conversion between different matrix formats, and compression of csr matrices.


In numerical analysis and scientific computing, a sparse matrix or sparse array is a matrix in which most of the elements are zero. There is no strict definition how many elements need to be zero for a matrix to be considered sparse but a common criterion is that the number of non-zero elements is roughly the number of rows or columns. By contrast, if most of the elements are nonzero, then the matrix is considered dense. The number of zero-valued elements divided by the total number of elements (e.g., m × n for an m × n matrix) is sometimes referred to as the sparsity of the matrix.

Those that support efficient modification, such as DOK (Dictionary of keys), LIL (List of lists), or COO (Coordinate list). These are typically used to construct the matrices.
Those that support efficient access and matrix operations, such as CSR (Compressed Sparse Row) or CSC (Compressed Sparse Column).

Specialized computers have been made for sparse matrices,[1] as they are common in the machine learning field.[2] Operations using standard dense-matrix structures and algorithms are slow and inefficient when applied to large sparse matrices as processing and memory are wasted on the zeros. Sparse data is by nature more easily compressed and thus requires significantly less storage. Some very large sparse matrices are infeasible to manipulate using standard dense-matrix algorithms.

What data types are you using? float, double, cuComplex, and cuDoubleComplex.


https://docs.nvidia.com/cuda/cusparse/index.html



Basic Linear Algebra for Sparse Matrices on NVIDIA GPUs
https://docs.nvidia.com/cuda-libraries/index.html
	

Source: https://docs.nvidia.com/cuda/archive/11.0/cuda-toolkit-release-notes/

An interim summary of the toolkit versions (ranging from 1.0 through 11.2.0) are shown in Table 3 below:

**Table 3: CUDA Toolkit Version Information**
<table>
<tr><td>Toolkit Version Number</td><td>Release Date</td></tr>
<tr><td>11.2.0</td><td>Dec 2020</td></tr>
<tr><td>11.1.1</td><td>Oct 2020</td></tr>
<tr><td>11.1.0</td><td>Sept 2020</td></tr>
<tr><td>11.0 Update 1</td><td>Aug 2020</td></tr>
<tr><td>11.0</td><td>May 2020</td></tr>
<tr><td>10.2</td><td>Nov 2019</td></tr>
<tr><td>10.1 Update 2</td><td>Aug 2019</td></tr>
<tr><td>10.1 Update 1</td><td>May 2019</td></tr>
<tr><td>10.1</td><td>Feb 2019</td></tr>
<tr><td>10.0</td><td>Sept 2018</td></tr>
<tr><td>9.2</td><td>May 2018</td></tr>
<tr><td>9.1</td><td>Dec 2017</td></tr>
<tr><td>9.0</td><td>Sept 2017</td></tr>
<tr><td>8.0 GA 2</td><td>Feb 2017</td></tr>
<tr><td>8.0 GA 1</td><td>Sept 2016</td></tr>
<tr><td>7.5</td><td>Sept 2015</td></tr>
<tr><td>7.0</td><td>March 2015</td></tr>
<tr><td>6.5</td><td>August 2014</td></tr>
<tr><td>6.0</td><td>April 2014</td></tr>
<tr><td>5.5</td><td>July 2013</td></tr>
<tr><td>5.0</td><td>Oct 2012</td></tr>
<tr><td>4.2</td><td>April 2012</td></tr>
<tr><td>4.1</td><td>Jan 2012</td></tr>
<tr><td>4.0</td><td>May 2011</td></tr>
<tr><td>3.2</td><td>Nov 2010</td></tr>
<tr><td>3.1</td><td>June 2010</td></tr>
<tr><td>3.0</td><td>March 2010</td></tr>
<tr><td>Open Computing Language (OpenCL) Release 1.0 </td><td>Sept 2009</td></tr>
<tr><td>2.3</td><td>June 2009</td></tr>
<tr><td>2.2</td><td>May 2009</td></tr>
<tr><td>2.1</td><td>Jan 2009</td></tr>
<tr><td>2.0</td><td>Aug 2008</td></tr>
<tr><td>1.1</td><td>Dec 2007</td></tr>
<tr><td>1.0</td><td>June 2007</td></tr>
</table>
Source: https://developer.nvidia.com/cuda-toolkit-archive

OpenCL and CUDA are both Graphics Processing Unit (GPU) programming frameworks, which leverage the use of GPUs. OpenCL is an open standard maintained by the Khronos Group consortium, whose members are listed here: https://www.khronos.org/members/list. CUDA is proprietary to NVIDIA.

The CUDA SDK v11.0 – v11.2 supports the Brain floating-point 16 bit (Bfloat16) format.

The Bfloat16 floating-point format for deep learning is an encoding format, which occupies 16 bits and represents a floating-point number. It is of the format [1:8:7], which has one sign bit, eight exponent bits, and seven mantissa bits plus one implicit mantissa bit. This differs from the IEEE Standard for Floating-Point Arithmetic (IEEE 754) 16-bit floating point (The format is assumed to have an implicit lead bit with value 1 unless the exponent field is stored with all zeros; hence, although there are only 10 bits of significand, there are 11 bits of significand precision), which was not designed for deep learning.

A principal benefit of Bfloat16 is to reduce the storage requirements and increase the computational speed of deep learning algorithms.



