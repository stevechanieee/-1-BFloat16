





Add the CUDA.jl Pkg, via the Pkg API:


<div style="background: #ffffff; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">julia<span style="color: #333333">&gt;</span> <span style="color: #008800; font-weight: bold">import</span> Pkg; Pkg<span style="color: #333333">.</span>add(<span style="background-color: #fff0f0">&quot;CUDA&quot;</span>)
</pre></div>

Precompile the Pkg and download the apropos CUDA toolkit:

<div style="background: #ffffff; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%"><span style="color: #333333">&lt;</span>pre<span style="color: #333333">&gt;</span>julia<span style="color: #333333">&gt;</span> <span style="color: #008800; font-weight: bold">using</span> CUDA
</pre></div>

<div style="background: #ffffff; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%">julia<span style="color: #333333">&gt;</span> CUDA<span style="color: #333333">.</span>versioninfo()<span style="color: #333333">&lt;/</span>pre<span style="color: #333333">&gt;</span>
</pre></div>




