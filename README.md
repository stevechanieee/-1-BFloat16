






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

**Table 1**
<table>
<thead class="thead" align="left">
<tr class="row">
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Version Number</th>
<th class="entry" align="center" valign="top" rowspan="1" colspan="1">Version Name</th>
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
2. cusparseXaxpyi
3. cusparseXgthr
4. cusparseXgthrz
5. cusparseXroti
6. cusparseXsctr

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

The CUDA SDK v11.0 – v11.2 supports Bfloat16.


