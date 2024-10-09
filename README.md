
# Overview

MicroEJ C Component: `com.microej.clibrary.llimpl#microvg-vglite`.

This component implements some Low-Level API (LLAPI) of MicroVG-1.x over VGLite library. 
Refer to the VEE Porting Guide > Vector Graphics > C Module to have more information on this module.

# MicroEJ VG Pack

This compoment is MicroEJ VG Pack dependent: it is compatible with a one or several MicroEJ VG Pack versions. The following table illustrates the compatibility:

| Component     | MicroEJ VG Pack |
| --------------| ----------------|
| 5.0.0         | 1.5.0           |
| 4.0.0         | 1.4.2           |
| [6.0.0-6.1.0] | [1.4.0 - 1.4.2[ |
| [5.0.0-5.0.1] | 1.3.0           |
| [4.0.0-4.0.4] | [1.2.0 - 1.3.0[ |
| [3.0.0-3.0.2] | [1.1.0 - 1.2.0[ |
| [1.0.0-2.0.0] | [1.0.0 - 1.1.0[ |

# Usage

Add the following line to your `module.ivy`:

    <dependency org="com.microej.clibrary.llimpl" name="microvg-vglite" rev="9.0.0"/>

2. Follow the **Usage** chapters of each component part (see VEE Porting Guide > Vector Graphics > C Module)

# Requirements

N/A.

# Dependencies

_All dependencies are retrieved transitively by MicroEJ Module Manager_.

# Source

N/A.

# Error Codes

The functions `LLVG_PAINTER_IMPL_drawPath` and `LLVG_PAINTER_IMPL_drawGradient` return an error code:

* `0`: success, the drawing is processed by the GPU.
* `-1`: VGLite library issue: the drawing is canceled.
* `-2`: The gradient cannot be processed (too many colors or VGLite library issue): the drawing is canceled.

# Restrictions

None.

---
_Copyright 2021-2024 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  
