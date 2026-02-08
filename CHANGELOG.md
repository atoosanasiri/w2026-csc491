---
title: Changelog
layout: default
nav_order: 100
---

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Site Configuration

- Added: `defaults` block in `_config.yml` to auto-apply `layout: default` to all pages under `docs/`
- Added: Sass `quiet_deps` and `silence_deprecations` to suppress `@import` deprecation warnings
- Removed: `jekyll-remote-theme` dependency; theme files are vendored locally
- Fixed: duplicate `sass:` block in `_config.yml` that was overriding deprecation settings

### Content

- Added: Cloud Architecture Design lecture with 7 child pages under `docs/course-material/cloud-architecture/`
- Added: Product Development Framework page
- Added: Course Material Styling Guide reference page
- Added: previous/next navigation buttons at the bottom of each cloud architecture child page
- Added: `has_toc: false` to cloud architecture index to suppress auto-generated TOC
- Changed: renamed cloud architecture child files to cleaner names (e.g., `thinking-like-architect.md` instead of `section-1-thinking-like-architect.md`)
- Changed: removed "Section X:" prefix from all cloud architecture child page titles and headings

### Styling

- Added: custom ILA classes in `_sass/custom/custom.scss`: `.lecture-title`, `.lecture-meta`, `.lecture-info`, `.section-header`, `.callout-box`, `.framework-box`
- Added: consistent ILA styling across all cloud architecture child pages using `.section-header`, `.callout-box`, `.framework-box`

### Earlier (pre-session)

- Added: Utilities pages (Color, Typography, Layout, Responsive Modifiers)
- Added: Markdown kitchen sink example page
- Added: Migration and upgrading guide
- Added: Course documentation structure
- Changed: updated README with CSC491 course information
- Changed: configured Just the Docs theme

## [1.0.0] - 2026-02-07

### Added
- Initial setup of CSC491 course website
- Just the Docs theme integration
- Basic course information pages

[Unreleased]: https://github.com/atoosanasiri/w2026-csc491/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/atoosanasiri/w2026-csc491/releases/tag/v1.0.0
