# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Interactive web application for a university-level Algebra and Geometry course (Computer Science track). Each module contains visual, hands-on demos showing how mathematical concepts apply directly to computing problems.

Deployed as a static site via **GitHub Pages** (Jekyll). No backend. All computation runs client-side in the browser.

## Tech Stack

- **Jekyll** — static site generator (GitHub Pages compatible)
- **Three.js** — 3D visualizations and WebGL
- **D3.js** — 2D charts, graphs, and vector field visualizations
- **Math.js** — symbolic and numeric linear algebra
- **Vanilla JS / Canvas 2D** — lightweight interactive demos

## Planned Module Structure

Each module lives in its own directory with a self-contained HTML page and JS logic:

```
/modulo-1-vectores/
/modulo-2-matrices/
/modulo-3-sistemas-ecuaciones/
/modulo-4-determinantes/
/modulo-5-eigenvalores/
/modulo-6-geometria/
/modulo-7-rotaciones/
_layouts/
_includes/
assets/
  js/
  css/
```

Each module page should be independently usable (no shared state between modules). Shared utilities (matrix helpers, canvas drawing primitives) go in `assets/js/`.

## Demos Planned per Module

| Module | Key Demo | Primary Library |
|--------|----------|-----------------|
| 1 — Vectors | Cosine similarity search, lighting, collision SAT | Canvas 2D |
| 2 — Matrices | 2D transform editor, graphics pipeline, image kernels, Markov chains | Canvas 2D / Three.js |
| 3 — Linear Systems | Network flow, polynomial interpolation, linear regression | D3.js / Math.js |
| 4 — Determinants | Sprite deformation, linear independence detector | Canvas 2D |
| 5 — Eigenvalues | PageRank simulator, PCA, SVD image compression | Math.js / D3.js |
| 6 — Analytic Geometry | Synthetic camera, ray casting, Bezier curves | Three.js / Canvas 2D |
| 7 — Rotations | Gimbal lock demo, quaternion SLERP | Three.js |

## Development

Since this is a Jekyll site served via GitHub Pages, local development uses:

```bash
bundle install          # first time only
bundle exec jekyll serve --livereload
# Site runs at http://localhost:4000
```

To add a new demo page, create a file with Jekyll front matter:

```yaml
---
layout: demo
title: "Titulo del Demo"
module: 2
---
```

## Design Principles

- Each demo must work without any server calls — all data and computation is local.
- Demos should be parametric: sliders, drag handles, and inputs that let students manipulate values and see results instantly.
- Mobile-friendly is a nice-to-have, but desktop-first is acceptable given the course context.
- Spanish is the primary language for UI text (course is taught in Spanish).
