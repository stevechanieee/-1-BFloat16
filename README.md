





Add the CUDA.jl Pkg, via the Pkg API:


<pre>julia> import Pkg; Pkg.add("CUDA")</pre>

Precompile the Pkg and download the apropos CUDA toolkit:

<pre>julia> using CUDA</pre>

<pre>julia> CUDA.versioninfo()</pre>




