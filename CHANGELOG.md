# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [9.0.1] - 2025-04-09

- Compatible with MicroEJ VG Pack 1.7.x.

### Changed

- Fetch the dependency CCO MicroVG 7.0.1.

### Fixed

- Fix the drawing of a BufferedVectorImage when applying a rotation.
- Fix the drawing bounds of the BufferedVectorImage's elements.
- Fix the drawing of gradient paths with zero or one color.
- Fix the use of clip when drawing a buffered vector image that contains vector images.
- Fix the clip when drawing a vector image in a buffered vector image.

### Removed

- Remove useless and invalid external field declaration.
- Remove dependency to a specific version of Freetype: the C module Freetype must be fetched independently.

## [9.0.0] - 2024-10-09

- Compatible with MicroEJ VG Pack 1.7.x.

### Changed

- Make this module compatible with MicroUI module 14.1.0.

## [8.0.1] - 2024-07-23

### Changed

- Fetch the dependency CCO MicroVG 6.0.1.

## [8.0.0] - 2024-07-19

- Compatible with MicroEJ VG Pack 1.6.x.

### Changed

- Anonymize the use of the Freetype library.
- Change the signature of all drawing functions: remove the parameters `x` and `y` (not backward compatible).
- Install the files in the `vg_vglite` directory.
- Increase the dependencies:
  - CCO MicroUI over VGlite 9.0.0.
  - CCO MicroVG 6.0.0.
  - CCO Freetype 3.0.0.
- Change the file structure:
  - Rename `bvi_vglite.h` to `vg_bvi_vglite.h`.
  - Rename `microvg_vglite_helper.h` to `vg_vglite_helper.h`.
  - Rename `LLVG_RAW_impl.c` to `vg_drawing_vglite_image.c`.
  - Rename `LLVG_vglite.c` to `LLVG_impl_vglite.c`.
  - Remove `LLVG_FONT_PAINTER_freetype_vglite.c`.
  - Add `LLVG_GRADIENT_impl_vglite.c`.
  - Add `vg_drawing_bvi.c`.
  - Add `vg_path_vglite.c`.
  - Add `vg_vglite_helper.c`.
- Rename functions:
  - `BVI_VGLITE_initialize` becomes `VG_BVI_VGLITE_initialize`.
  - `BVI_VGLITE_adjust_new_image_characteristics` becomes `VG_BVI_VGLITE_adjust_new_image_characteristics`.
  - `BVI_VGLITE_initialize_new_image` becomes `VG_BVI_VGLITE_initialize_new_image`.
  - `BVI_VGLITE_free_resources` becomes `VG_BVI_VGLITE_free_resources`.
  - `BVI_VGLITE_add_draw_path` becomes `VG_BVI_VGLITE_add_draw_path`.
  - `BVI_VGLITE_add_draw_gradient` becomes `VG_BVI_VGLITE_add_draw_gradient`.
  - `BVI_VGLITE_add_draw_image` becomes `VG_BVI_VGLITE_add_draw_image`.
  - `MICROVG_VGLITE_report_error` becomes `VG_VGLITE_HELPER_report_error`.
  - `MICROVG_VGLITE_handle_error` becomes `VG_VGLITE_HELPER_handle_error`.
  - `MICROVG_VGLITE_HELPER_get_blend` becomes `VG_VGLITE_HELPER_get_blend`.
  - `MICROVG_VGLITE_HELPER_get_fill_rule` becomes `VG_VGLITE_HELPER_get_fill_rule`.
  - `MICROVG_VGLITE_HELPER_get_microvg_blend` becomes `VG_VGLITE_HELPER_get_microvg_blend`.
  - `MICROVG_VGLITE_HELPER_get_microvg_fill_rule` becomes `VG_VGLITE_HELPER_get_microvg_fill_rule`.
  - `MICROVG_VGLITE_HELPER_to_vg_lite_gradient` becomes `VG_VGLITE_HELPER_to_vg_lite_gradient`.

### Removed

- Remove `VG_DRAWING_VGLITE_prepare_matrix()` (use generic function `VG_HELPER_prepare_matrix()` instead).
- Remove the VGLite specific function to draw a string with Freetype: `VG_DRAWING_VGLITE_draw_string()` and its associated typedef `VG_DRAWING_VGLITE_draw_glyph_t`.
- Remove the specific `drawString` painter over Freetype with VGLite backend (use the generic painter instead).

## [7.0.1] - 2024-04-11

- Compatible with MicroEJ VG Pack 1.5.x.

### Fixed

- Fix the drawing of a VG RAW image in a BVI with a clip.

## [7.0.0] - 2024-02-15

- Compatible with MicroEJ VG Pack 1.5.x.

### Changed

- Make the CCO compatible with VG pack 1.5.0 and higher.
- Make the CCO compatible with the UI Pack 14.0.0 (CCO MicroVG 5.0.0 and MicroUI-VGLite 8.0.0).

### Fixed

- Fix the release of the BVI resources.
- Fix the storing of color matrices in the BVI.

## [6.1.1] - 2023-11-13

- Compatible with MicroEJ VG Pack 1.4.2.

### Changed

- Make the CCO compatible with VG pack 1.4.2 and higher.

### Fixed

- Fix dynamic paths larger than 64 KB.
- Fix some comments.
- Fix the dynamic path drawing on RT1170 (use the same quality of paths as vector images).
- Fix the path drawing on RT1170 (disable the color pre-multiplication).
- Fix the rendering of some blending modes on RT1170 by disabling the GPU pre-multiplication when required.

## [6.1.0] - 2023-09-21

### Added

- Add the compatibility with VGLite `3.0.15_rev7`.

### Fixed

- Fix the use of the define `VG_BLIT_WORKAROUND` (useless).
- Fix the GPU deactivation when a drawing is not performed for any reason.

## [6.0.0] - 2023-07-21

- Compatible with MicroEJ VG Pack 1.4.x.

### Added

- Add support for DST_OUT and PLUS blend modes (VG Pack 1.4.0).

### Changed

- Make the CCO compatible with VG pack 1.4.0 and higher.
- Make CCO compatible with the CCO `microui-vglite#7.0.0` (not backward compatible).

### Fixed

- Fix the SystemView log identifiers.
- Remove the include of the unknown header file `trace_vglite.h` (require a re-build of FreeType library).

## [5.0.1] - 2023-06-08

### Fixed

- Fix performing drawings when the clip is disabled.

## [5.0.0] - 2023-05-10

- Compatible with MicroEJ VG Pack 1.3.x.

### Added

- Add the compatibility with multiple Graphics Context output formats (UI Pack 13.5.0).
- Add the implementation of all MicroUI, Drawing and MicroVG drawings in MicroVG BufferedVectorImage (VG Pack 1.3.0).
- Add incident reporting with drawing log flags from UI Pack 13.5.0.

### Changed

- Make the CCO compatible with UI pack 13.5.0 and higher.
- Make the CCO compatible with VG pack 1.3.0 and higher.
- Merge BufferedVectorImage and RAW formats.
- Simplify the gradient modification according to the caller translation.

### Removed

- Remove `LLVG_BVI_impl.c`: code is merged in `LLVG_RAW_impl.c`.
- Remove (move) some utility functions to CCO MicroUI-VGLite.
- Remove "draw String" native functions implementation (implemented in CCO MicroVG).

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

- Compatible with MicroEJ VG Pack 1.2.x.

### Added

- Add the compatibility with VGLite `3.0.15_rev4` (not backward compatible).
- Add the VectorImage in binary format management (RAW format).
- Add loading of VectorImage from external resource system.

### Changed

- Make the CCO compatible with VG pack 1.2.0 and higher.
- Reduce the gradient footprint in BufferedVectorImage.
- Harmonize the use of `vg_drawer.h` functions (instead of `VG_DRAWER_drawer_t` functions) in BufferedVectorImage.
- Use the VGLite API to initialize the VGLite paths.
- Use the global fields "VGLite paths" instead of functions fields (prevent dynamic allocation on task stack).

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

- Compatible with MicroEJ VG Pack 1.1.x.

### Added

- Add the buffered vector image feature (BVI).

### Changed

- Make the CCO compatible with VG pack 1.1.0 and higher.
- Manage the closed fonts.
- Configure freetype CCO from `microvg_configuration.h` header file.
- Move `ftvglite.c` and `ftvglite.h` to freetype CCO.
- Extract text layout to microvg CCO.
- Get fill rule configuration from each glyph `FT_Outline->flags` instead of defaulting it to `VG_LITE_FILL_EVEN_ODD`.
- Use the MicroUI over VGLite's Vectorial Drawer mechanism.
- Join character bboxes at baseline for drawStringOnCircle.

### Fixed

- Fix performance issues in drawString.

## [2.0.0] - 2022-05-13

### Changed

- Follow the new specification of VGLite `3.0.11_rev3 vg_lite_set_scissor()`.

## [1.0.0] - Unreleased

### Added

- CCO creation.
- Initial revision based on `com.microej.clibrary.llimpl#vector-font-vglite#1.0.0`.
- Add UTF16 characters parsing in `LLVG_FONT_PAINTER_IMPL_draw_string()` and `LLVG_FONT_PAINTER_IMPL_draw_string_on_circle()`.
- Add support of multilayers glyphs, colored emoji.

---
_Copyright 2021-2025 MicroEJ Corp. All rights reserved._\
_Use of this source code is governed by a BSD-style license that can be found with this software._
