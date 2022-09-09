# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 3.0.2 - 2022-09-09

### Fixed

  - Fix the dependency to the CCO Freetype.

## 3.0.1 - 2022-09-08

### Fixed

  - Fix the dependency to the CCO Freetype.

## 3.0.0 - 2022-09-02

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
  
## 2.0.0 - 2022-05-13

### Changed

  - Follow the new specification of VG-Lite `3.0.11_rev3 vg_lite_set_scissor()`.

## 1.0.0 - Unreleased

### Added

  - CCO creation.
  - Initial revision based on `com.microej.clibrary.llimpl#vector-font-vglite#1.0.0`.
  - Add UTF16 characters parsing in `LLVG_FONT_PAINTER_IMPL_draw_string()` and `LLVG_FONT_PAINTER_IMPL_draw_string_on_circle()`.
  - Add support of multilayers glyphs, colored emoji.
 
---
_Copyright 2021-2022 MicroEJ Corp. All rights reserved._  
_Use of this source code is governed by a BSD-style license that can be found with this software._  
