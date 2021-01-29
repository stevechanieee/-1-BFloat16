





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
 v"11.0.3"
```

Reference: https://docs.nvidia.com/cuda/archive/11.0/cuda-toolkit-release-notes/

Note the deprecations at this version:

cusparse<t>gemmi()
cusparseXaxpyi
cusparseXgthr
cusparseXgthrz
cusparseXroti
cusparseXsctr
 
Note the version information for the various components, as the constituent components in the toolkit are versioned independently as of CUDA v11. By way of example, Table 1 below reflects the independent versioning:

<table cellpadding="4" cellspacing="0" frame="border" border="1" rules="all">
<caption><span >Table 1. CUDA 11 Component Versions</span></caption>
<thead class="thead" align="left">
<tr class="row">
<th class="entry" align="center" valign="top" id="d54e1044" rowspan="1" colspan="1">Component Name</th>
<th class="entry" align="center" valign="top" id="d54e1047" rowspan="1" colspan="1">Version Information</th>
<th class="entry" align="center" valign="top" id="d54e1050" rowspan="1" colspan="1">Supported Architectures</th>
</tr>
</thead>
<tbody class="tbody">
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA Runtime (cudart)</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">cuobjdump</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUPTI</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA Demo Suite</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.167</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA GDB</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA Memcheck</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA NVCC</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA nvdisasm</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA NVML Headers</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.167</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA nvprof</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA nvprune</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA NVRTC</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA NVTX</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.167</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA NVVP</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA Samples</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA Compute Sanitizer API</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA cuBLAS</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.2.0.252</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA cuFFT</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">10.2.1.245</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA cuRAND</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">10.2.1.245</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA cuSOLVER</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">10.6.0.245</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA cuSPARSE</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.1.1.245</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA NPP</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.1.0.245</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">CUDA nvJPEG</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.1.1.245</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">Nsight Eclipse Plugins</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">11.0.221</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">Nsight Compute</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">2020.1.2.4</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">Nsight Windows NVTX</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">1.21018621</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">Nsight Systems</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">2020.3.2.6</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">Nsight Visual Studio Edition (VSE)</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">2020.1.2.20203</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64 (Windows)</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">NVIDIA Linux Driver</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">450.51.06</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64, POWER, Arm64</td>
</tr>
<tr class="row">
<td class="entry" valign="top" headers="d54e1044" rowspan="1" colspan="1">NVIDIA Windows Driver</td>
<td class="entry" valign="top" headers="d54e1047" rowspan="1" colspan="1">451.82</td>
<td class="entry" valign="top" headers="d54e1050" rowspan="1" colspan="1">x86_64 (Windows)</td>
</tr>
</tbody>
</table>
