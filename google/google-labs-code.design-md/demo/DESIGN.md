---
version: alpha
name: Harbor
description: Demo DESIGN.md for the harness-engineering-collection
colors:
  primary: "#13293D"
  secondary: "#4A6FA5"
  tertiary: "#3CAEA3"
  neutral: "#F4F7F5"
  on-primary: "#F4F7F5"
  on-tertiary: "#0B1F22"
typography:
  h1:
    fontFamily: Fraunces
    fontSize: 3rem
    fontWeight: 600
    lineHeight: 1.1
  body-md:
    fontFamily: Inter
    fontSize: 1rem
    fontWeight: 400
    lineHeight: 1.5
  label-caps:
    fontFamily: Inter
    fontSize: 0.75rem
    fontWeight: 600
    letterSpacing: 0.08em
rounded:
  sm: 4px
  md: 8px
spacing:
  sm: 8
  md: 16
components:
  button-primary:
    backgroundColor: "{colors.tertiary}"
    textColor: "{colors.on-tertiary}"
    rounded: "{rounded.md}"
    padding: 12px
  button-primary-hover:
    backgroundColor: "{colors.secondary}"
---

## Overview

Calm maritime minimalism. Deep harbor ink for structure, a single teal
accent for interaction, warm off-white as the foundation. The system reads
as a quiet, trustworthy dashboard — nautical without being literal.

## Colors

Rooted in high-contrast neutrals plus one driving accent.

- **Primary (#13293D):** Harbor ink — headlines, core text, dark surfaces.
- **Secondary (#4A6FA5):** Slate blue — borders, captions, hover states.
- **Tertiary (#3CAEA3):** The sole interaction driver.
- **Neutral (#F4F7F5):** Warm sea-foam foundation, softer than pure white.

## Typography

Two-family system: Fraunces for editorial weight in headlines, Inter for
neutral, legible body and labels.

- **h1:** Fraunces 3rem/600 — section anchors.
- **body-md:** Inter 1rem/400 — primary reading.
- **label-caps:** Inter 0.75rem/600, tracked — metadata and tags.

## Layout

8px base spacing scale. Components compose from `spacing.sm` (8) and
`spacing.md` (16) multiples.

## Elevation & Depth

Minimal. Surfaces rely on hairline borders (`colors.secondary` at low
opacity) over shadows. A single subtle shadow is reserved for floating
layers (toasts, menus).

## Shapes

- **sm (4px):** inputs, tags.
- **md (8px):** buttons, cards.

## Components

- **button-primary:** teal ground, ink text, 8px radius, 12px padding.
- **button-primary-hover:** swaps to slate blue secondary.

## Do's and Don'ts

- **Do** keep tertiary to one interaction per surface.
- **Do** use label-caps only for genuine metadata.
- **Don't** introduce a second accent color.
- **Don't** use Fraunces below 1.25rem — it loses contrast at body sizes.
