# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [6.1.1] - 2023-11-13

### Fixed

  - Fix dynamic paths larger than 64 KB.
  - Fix some comments.
  - Fix the dynamic path drawing on RT1170 (use the same quality of paths as vector images). 
  - Fix the path drawing on RT1170 (disable the color pre-multiplication).
  - Fix the rendering of some blending modes on RT1170 by disabling the GPU pre-multiplication when required.

## [6.1.0] - 2023-09-21

### Added

  - Add the compatibility with VG-Lite `3.0.15_rev7`.

### Fixed

  - Fix the use of the define `VG_BLIT_WORKAROUND` (useless).
  - Fix the GPU deactivation when a drawing is not performed for any reason.

## [6.0.0] - 2023-07-21

### Added

  - Add support for DST_OUT and PLUS blend modes (VG Pack 1.4.0).

### Changed

  - Make CCO compatible with the CCO `microui-vglite#7.0.0` (not backward compatible).

### Fixed

  - Fix the SystemView log identifiers.
  - Remove the include of the unknown header file `trace_vglite.h` (require a re-build of FreeType library).
  
### Migration Guide

  - Follow the migration steps of CCO MicroUI-VGLite 7.0.0.
  - [VEE Port configuration project] 
  		- CCO MicroVG-VGLite 6.0.0.
  - Build the VEE Port, the Freetype library (in the case of a dedicated project) and the BSP.
  
## [5.0.1] - 2023-06-08

### Fixed

  - Fix performing drawings when the clip is disabled.

## [5.0.0] - 2023-05-10

### Added

  - Add the compatibility with multiple Graphics Context output formats (UI Pack 13.5.0).
  - Add the implementation of all MicroUI, Drawing and MicroVG drawings in MicroVG BufferedVectorImage (VG Pack 1.3.0).
  - Add incident reporting with drawing log flags from UI Pack 13.5.0.

### Changed

  - Make the CCO compatible with UI pack 13.5.0 and higher.
  - Make the CCO compatible with VG pack 1.3.0 and higher.
  - Merge BufferedVectorImage and RAW formats.
  - Simplify the gradient modification according the caller translation.

### Removed

  - Remove `LLVG_BVI_impl.c`: code is merged in `LLVG_RAW_impl.c`.
  - Remove (move) some utility functions to CCO MicroUI-VGLite.
  - Remove "draw String" native functions implementation (implemented in CCO MicroVG).

### Migration Guide

  - Follow the migration steps of CCO MicroVG 3.0.0
  - [VEE Port configuration project] 
  		- Fetch CCO MicroVG-VGLite 5.0.0.
  - [BSP project] 
  		- Delete the properties file `cco_microvg-vglite.properties`.
  		- Delete the C files `LLVG_BVI_impl.c` and `LLVG_PATH_PAINTER_vglite.c` and remove them from the C project configuration.
  		- In the C project configuration, include the new C file `ui_drawing_bvi.c`, ``vg_drawing_bvi.c`, `vg_drawing_vglite.c`.
  		- In the C project configuration, set the define `LLUI_GC_SUPPORTED_FORMATS=2` to enable the BufferedVectorImage support.
  - Build the VEE Port, the Freetype library (if case of dedicated project) and the BSP.

## [4.0.4] - 2023-03-15

### Fixed

  - Fix the path to render during a "path data" animation:
  	- when at least one animation is applied: the command buffer length and the path bounding box can be different than the original path, 
  	- when no animation is applied: the original path must be drawn. 

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
