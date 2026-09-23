---
name: latex-elegantbook-polish
description: Optimize Chinese LaTeX books, lecture notes, and long-form mathematical documents into an ElegantBook-inspired style while preserving their content; use when the user asks to beautify, standardize, compile, preview, or open such a document in an editor.
---

# ElegantBook-style LaTeX polishing

Produce a clean, maintainable Chinese book layout inspired by ElegantBook. Preserve the author's mathematical and textual content unless the user separately asks for proofreading or correction.

## Inspect first

- Locate the main `.tex` file by checking `\documentclass`, `\begin{document}`, and inclusion relationships. Do not assume the largest file is the entry point.
- Read local project instructions and inspect existing classes, packages, fonts, bibliography, images, and build configuration.
- Check whether XeLaTeX and `latexmk` are available. Chinese documents should normally use XeLaTeX unless the project already requires another engine.
- Preserve unrelated edits and established custom commands.

## Choose the least disruptive approach

- If the project already has a stable book class or custom design, layer compatible styling onto it instead of replacing the class.
- For plain Chinese `article` documents that are clearly book-like, prefer `ctexbook` with `openany` and convert manual chapter/section text into semantic commands.
- Treat “仿照 ElegantBook” as a visual direction, not a requirement to depend on `elegantbook.cls`. Use the actual class only when the user explicitly requests it or the project already depends on it.
- Keep the document portable: prefer TeX Live fonts and packages; avoid machine-specific absolute paths.

## Visual system

Adapt these choices to the document rather than copying them mechanically:

- Use a restrained blue-green primary color, dark ink text, and a warm accent color.
- Establish semantic `\chapter`, `\section`, and optional exercise headings with consistent numbering and table-of-contents entries.
- Add balanced A4 geometry, comfortable Chinese line spacing, two-em paragraph indentation, and modest paragraph spacing.
- Use `fancyhdr` for understated running heads and page numbers.
- Use `titlesec`, `tikz`, or `tcolorbox` for chapter rules, section number badges, and compact definition/theorem/example labels.
- Keep mathematics in a dedicated Unicode math font such as STIX Two Math when compatible.
- Add a cover and contents page only when the document is long-form and they improve navigation. Do not invent author, institution, or publication metadata.
- Ensure every package used by a custom command is loaded. In particular, commands containing `\tikz` require TikZ.

## Editing constraints

- Do not silently rewrite formulas, theorem statements, exercise answers, references, or notation.
- Replace manual visible headings with semantic LaTeX commands when the mapping is unambiguous.
- Preserve numbering printed in the source when changing it could invalidate cross-references; introduce styling macros around it if necessary.
- Keep style definitions near the preamble and give reusable colors/macros descriptive names.
- Fix compatibility defects revealed by compilation, such as missing glyphs, by using LaTeX symbols or compatible fonts rather than changing meaning.

## Verify

1. Compile the main file with `latexmk -xelatex -interaction=nonstopmode -file-line-error`.
2. Resolve LaTeX errors, missing characters, duplicate destinations, and actionable package warnings introduced by the change.
3. Recompile until references and the table of contents stabilize.
4. Render and visually inspect at least one title/chapter page and one dense body page when PDF rendering tools are available. Check clipping, hierarchy, color contrast, equation width, headers, and page numbers.
5. Remove temporary preview images created only for inspection; keep the requested PDF and normal build artifacts unless the user prefers a clean source tree.

## Editor handoff

When the user asks to open the result, open the project folder and position the editor at the main `.tex` file. Prefer the available application-control capability; if unavailable, use the existing editor CLI without installing software. Verify success when the environment exposes a reliable window or process status.

Report the main source path, generated PDF path, compilation result, and the most important formatting changes.
