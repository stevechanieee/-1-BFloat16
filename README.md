





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
 v"11.0.0"
```
