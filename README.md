





Add the CUDA.jl Pkg, via the Pkg API:

<code>julia> import Pkg; Pkg.add("CUDA")</code>

Precompile the Pkg and download the apropos CUDA toolkit:

<code>julia> using CUDA</code>

<code>julia> CUDA.versioninfo()</code>
