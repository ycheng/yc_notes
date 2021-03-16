
* download app from web site and don't use ubuntu pkg.
  * https://discourse.julialang.org/t/bug-involving-permutedims-function/43492/1

Sample Source:
```
using Pkg
# Pkg.add("Flux")
# Pkg.add("Metalhead")
# Pkg.add("ImageMagick")
# Pkg.add("CUDA")
println("m1")

using Flux, CUDA
using Metalhead
using Metalhead: classify

println("m2")


img = load("Elep.jpg")
println("m3")

vgg = VGG19()
vgg = VGG19() |> gpu

println("m4")

r = classify(vgg, img)
println("m5")
print(r)


```
