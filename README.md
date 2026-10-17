# gltfheader

An R header-only package containing the unmodified cgltf v1.15 loader for loading GLTF and GLB files. There are no R functions or compiled libraries in this package.

Install locally with `R CMD INSTALL /path/to/gltfheader`.
Consumer R packages add `gltfheader (>= 1.15.0)` to `LinkingTo` in DESCRIPTION
and include `<cgltf.h>`. Define `CGLTF_IMPLEMENTATION` before the include in
exactly one C or C++ translation unit per downstream package:

```c
#define CGLTF_IMPLEMENTATION
#include <cgltf.h>
```
