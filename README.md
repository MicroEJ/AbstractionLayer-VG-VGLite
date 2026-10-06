![ARCH](https://shields.microej.com/endpoint?url=https://repository.microej.com/packages/badges/arch_7.16.json)

# Overview

This Abstraction Layer implements the drawings of the MicroVG Low Level API, described in [LLVG: Vector Graphics](https://docs.microej.com/en/latest/VEEPortingGuide/appendix/llapi.html#llvg-vectorgraphics), over the Vivante VGLite library.
It provides the drawing functions that the MicroVG Abstraction Layer leaves to a GPU Abstraction Layer.
See the [MicroVG Over VGLite](https://docs.microej.com/en/latest/VEEPortingGuide/vgCco.html#section-vg-c-module-microvg-vglite) section of the MicroEJ documentation.

This Abstraction Layer is tied to the MicroEJ VG Pack: the versions it is compatible with are listed in the [compatibility](https://docs.microej.com/en/latest/VEEPortingGuide/vgReleaseNotes.html#c-modules-compatibility-version) tables of the documentation.
The badge above gives the oldest MicroEJ Architecture it supports, not the latest one: the [MicroEJ Architecture Compatibility Version](https://docs.microej.com/en/latest/VEEPortingGuide/uiReleaseNotes.html#microej-architecture-compatibility-version) tables list the Architectures of each UI Pack version.

# Usage

1. Add the sources of this Abstraction Layer to the BSP of the VEE Port, in either of these two ways:

   - From the MicroEJ repository: install the `.cco` archive of the version the VEE Port needs, as the [installation guide](https://docs.microej.com/en/latest/VEEPortingGuide/appendix/cmodules.html) describes.
     The headers land in `bsp/vee/port/vg_vglite/inc` and the sources in `bsp/vee/port/vg_vglite/src`.
   - From GitHub: add the [GitHub repository](https://github.com/MicroEJ/AbstractionLayer-VG-VGLite) to the BSP of the VEE Port as a git submodule, at the tag of the version the VEE Port needs.
     The VEE Port chooses the folder of the submodule, and either of these two layouts works.
     A flat folder sits beside the other components of the BSP:

     ```sh
     git submodule add https://github.com/MicroEJ/AbstractionLayer-VG-VGLite.git bsp/vee/port/vg_vglite
     git -C bsp/vee/port/vg_vglite checkout <version>
     ```

     A folder grouped by domain sits under the folder of the other components of the same domain:

     ```sh
     git submodule add https://github.com/MicroEJ/AbstractionLayer-VG-VGLite.git bsp/vee/port/vg/VG-VGLite
     git -C bsp/vee/port/vg/VG-VGLite checkout <version>
     ```

     The headers then sit in `<folder>/src/main/c/inc` and the sources in `<folder>/src/main/c/src`, where `<folder>` is the folder of the submodule.
     A copy of these sources in the VEE Port repository works as well.

   Then add the folder of the headers to the include paths of the BSP project, and the files of the folder of the sources to its sources.

2. When the VEE Port moves to another version of this Abstraction Layer, follow the [MicroVG migration guide](https://docs.microej.com/en/latest/VEEPortingGuide/vgMigrationGuide.html).

# Requirements

None.

# Validation

This Abstraction Layer is tested on the following boards:

- MIMXRT595-EVK, with the VGLite library 3.0.15_rev7.

# MISRA Compliance

This Abstraction Layer is MISRA-compliant (MISRA C:2012) with some noted exceptions.
It has been verified with Cppcheck v2.13.
Here is the list of deviations from the MISRA standard:

| Deviation  | Category  | Justification                                                                                                                                                   |
|:----------:|:---------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Rule 2.3   | Advisory  | A type can be defined at API level and not used by the application.                                                                                             |
| Rule 2.4   | Advisory  | A tag can be defined at API level and not used by the application.                                                                                              |
| Rule 2.5   | Advisory  | A macro can be defined at API level and not used by the application.                                                                                            |
| Rule 2.7   | Advisory  | Wrong detection: the parameter is unused only when `VG_FEATURE_RAW_EXTERNAL` is set.                                                                            |
| Rule 5.9   | Advisory  | The same static function name can be used in several C files.                                                                                                   |
| Rule 8.4   | Required  | The compatible declarations are the VG Pack's functions.                                                                                                        |
| Rule 8.7   | Advisory  | The LLAPI functions require external linkage, but cppcheck cannot detect their invocation by the Pack.                                                          |
| Rule 11.3  | Required  | Each cast targets the structure or array type that the vector image data is known to hold (a block, an animation, a transformation), which factorizes the code. |
| Rule 11.4  | Advisory  | An address is converted to an integer to compute the end of a path or the memory offset applied to the addresses of an image.                                   |
| Rule 11.5  | Advisory  | A `void *` is converted to the object type it is known to point to (a vector image, an animation, a path, a numeric array), for code genericity.                |
| Rule 11.8  | Required  | The `const` qualifier is removed when a function or a structure requires a non-`const` pointer, or to get the address of a block.                               |
| Rule 17.2  | Required  | The recursion is limited to one level.                                                                                                                          |
| Rule 17.3  | Mandatory | The implicitly declared functions are the UI Pack's and VG Pack's functions.                                                                                    |
| Rule 17.8  | Advisory  | A parameter is modified for convenience.                                                                                                                        |
| Rule 18.4  | Advisory  | Pointer arithmetic is used to reach the data that follows a header in a vector image, or to apply a memory offset.                                              |
| Rule 18.8  | Required  | The size of the arrays is a constant defined by a macro.                                                                                                        |

# Dependencies

- The MicroVG Abstraction Layer.
- The MicroUI over VGLite Abstraction Layer, whose functions this Abstraction Layer calls.
- The VGLite library.

# Changelog

The changes of this Abstraction Layer are listed in the [public changelog of the MicroEJ VG Pack](https://docs.microej.com/en/latest/VEEPortingGuide/vgChangeLog.html), section `C Module VGLite`.

# Source

- `vg_drawing_vglite.h`, `vg_drawing_vglite.c`: the MicroVG drawing functions over VGLite.
- `vg_drawing_vglite_image.c`: the drawing of a vector image.
- `vg_bvi_vglite.h`, `vg_drawing_bvi.c`, `ui_drawing_bvi.c`: the drawings over a BufferedVectorImage.
- `LLVG_GRADIENT_impl_vglite.c`: the linear gradient.
- `vg_path_vglite.c`: the functions of `vg_path.h` over VGLite.
- `vg_vglite_helper.h`, `vg_vglite_helper.c`: the helpers shared by the other files.

# Restrictions

None.

---
_Copyright 2021-2026 MicroEJ Corp._\
_Use of this source code is governed by a BSD-style license that can be found with this software._
