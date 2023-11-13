
# Overview

This component contains the Low-Level API (LLAPI) of MicroVG implementation over VGLITE.

# Usage

Add the following line to your `module.ivy`:

    <dependency org="com.microej.clibrary.llimpl" name="microvg-vglite" rev="6.1.1"/>

# Requirements

N/A.

# Dependencies

_All dependencies are retrieved transitively by MicroEJ Module Manager_.

# Source

N/A.

# Error Codes

The functions `LLVG_PAINTER_IMPL_drawPath` and `LLVG_PAINTER_IMPL_drawGradient` return an error code:

* `0`: success, the drawing is processed by the GPU.
* `-1`: VG-Lite library issue: the drawing is canceled.
* `-2`: The gradient cannot be processed (too many colors or VG-Lite library issue): the drawing is canceled.

# Restrictions

None.

---
_Copyright 2021-2022 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  
