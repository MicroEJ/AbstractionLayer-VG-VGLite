# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [4.0.3] - 2023-02-03

### Fixed

  - Fix the synchronization with the Graphics Engine when a VG drawing is not performed (draw path, draw gradient, draw string).

## [4.0.2] - 2023-01-17

### Fixed

  - Fix the interface between Freetype and MicroVG (remove useless parameter).

## [4.0.1] - 2023-01-02

### Fixed

  - Fix the drawing of RAW images with multiple gradients in BufferedVectorImage.
  - Fix a deadlock when drawing an empty BufferedVectorImage.

## [4.0.0] - 2022-12-30

### Added

  - Add the compatibility with VG-Lite `3.0.15_rev4` (not backward compatible).
  - Add the VectorImage in binary format management (RAW format).
  - Add loading of VectorImage from external resource system.

### Changed

  - Reduce the gradient footprint in BufferedVectorImage.
  - Harmonize the use of `vg_drawer.h` functions (instead of `VG_DRAWER_drawer_t` functions) in BufferedVectorImage.
  - Use the VG-Lite API to initialize the VG-Lite paths.
  - Use the global fields "VG-Lite paths" instead of functions fields (prevent dynamic allocation on task stack). 

### Fixed

  - Fix the drawing of a text in a BufferedVectorImage: do not wakeup the GPU. 
  - Fix the constants used in `get_command_parameter_number` function (no side-effect).  

## [3.0.2] - 2022-09-09

### Fixed

  - Fix the dependency to the CCO Freetype.

## [3.0.1] - 2022-09-08

### Fixed

  - Fix the dependency to the CCO Freetype.

## [3.0.0] - 2022-09-02

### Added

  - Add the buffered vector image feature (BVI).
 
### Changed 

  - Manage the closed fonts.
  - Configure freetype CCO from `microvg_configuration.h` header file.
  - Move `ftvglite.c` and `ftvglite.h` to freetype CCO.
  - Extract text layout to microvg CCO.  
  - Get fill rule configuration from each glyph `FT_Outline->flags` instead of defaulting it to `VG_LITE_FILL_EVEN_ODD`.
  - Use the MicroUI over VG-Lite's Vectorial Drawer mechanism.
  - Join character bboxes at baseline for drawStringOnCircle.
  
### Fixed
  
  - Fix performance issues in drawString.
  
## [2.0.0] - 2022-05-13

### Changed

  - Follow the new specification of VG-Lite `3.0.11_rev3 vg_lite_set_scissor()`.

## [1.0.0] - Unreleased

### Added

  - CCO creation.
  - Initial revision based on `com.microej.clibrary.llimpl#vector-font-vglite#1.0.0`.
  - Add UTF16 characters parsing in `LLVG_FONT_PAINTER_IMPL_draw_string()` and `LLVG_FONT_PAINTER_IMPL_draw_string_on_circle()`.
  - Add support of multilayers glyphs, colored emoji.
 
---
_Copyright 2021-2023 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  
