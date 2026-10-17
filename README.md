# gltfheader

An R header-only package containing the unmodified cgltf v1.15 loader.
See inst/UPSTREAM for the pinned commit and checksum, and
inst/licenses/cgltf-MIT.txt for the upstream license.
There are no R functions or compiled libraries in this package.

Install locally with `R CMD INSTALL /path/to/gltfheader`.
Consumer R packages add `gltfheader (>= 1.15.0)` to `LinkingTo` in DESCRIPTION
and include `<cgltf.h>`. Define `CGLTF_IMPLEMENTATION` before the include in
exactly one C or C++ translation unit per consumer library:

```c
#define CGLTF_IMPLEMENTATION
#include <cgltf.h>
```

Consumers compiling the implementation must retain the MIT notice in their
binary distributions. The installed notice is at
`system.file("licenses", "cgltf-MIT.txt", package = "gltfheader")`.
No runtime dependency on the R namespace is needed.

The smoke program parses and validates a minimal glTF scene and checks a node
transform. Test both C and C++ using the installed headers:

```sh
include=$(Rscript -e 'cat(system.file("include", package="gltfheader"))')
cc -std=c99 -I"$include" tools/smoke-test.c -lm -o /tmp/gltfheader-c
/tmp/gltfheader-c
c++ -x c++ -I"$include" tools/smoke-test.c -o /tmp/gltfheader-cpp
/tmp/gltfheader-cpp
```
