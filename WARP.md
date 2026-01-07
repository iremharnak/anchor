# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project overview

This repository is a single-page static marketing/landing site for the "Anchor" mental wellness experience ("Quiet mental support for emotionally demanding moments"). It is implemented as a standalone HTML file styled with Tailwind CSS via the CDN and Google Fonts.

## Code and architecture

- **Entry point:** `index.html` is the only source file and contains the full page markup, Tailwind configuration, and styling.
- **Styling:**
  - Tailwind CSS is loaded from the CDN (`<script src="https://cdn.tailwindcss.com?...">`).
  - A small inline `tailwind.config` script extends the theme with:
    - Custom colors: `primary`, `background-light`, `background-dark`, `text-main`, `text-muted`.
    - `fontFamily.display` set to `Manrope`.
    - Custom `borderRadius` values.
  - Typography uses the `Manrope` font loaded from Google Fonts.
- **Theming / dark mode:**
  - The `<html>` root element is given a `class="light"` by default; Tailwind is configured with `darkMode: "class"`.
  - The `<body>` tag uses paired light/dark utility classes (e.g. `bg-background-light dark:bg-background-dark`) so applying a `dark` class to the `<html>` element will switch the theme.
  - There is no JavaScript in this repo to toggle dark mode; any theme switching must be done externally (e.g., by editing the HTML or injecting a script).
- **Layout structure (high level):**
  - **Header / wordmark:** Simple text header displaying the brand name "Anchor".
  - **Hero section:** Main headline and subheading that describe the value proposition, plus a primary CTA link that scrolls to the email capture section (`href="#cta"`).
  - **Body copy:** Copy blocks explaining the emotional context and a bullet list for "This is for you if".
  - **"What this is" section:** List of short, affirmative value points with Material Symbols icons and Tailwind-styled layout.
  - **"What this is not" section:** List of items clarifying what the experience is not (e.g. not therapy, not journaling), again using Material Symbols icons.
  - **CTA / email capture (`#cta` section):**
    - A centered form with label, email input, and submit button.
    - The form posts via `method="POST"` to `action="YOUR_FORM_ENDPOINT_HERE"` — this is a placeholder and must be replaced with a real endpoint before production use.
    - Includes brief copy around inbox respect and a disclaimer that this is not therapy or medical care.
  - **Footer:** Copyright notice for "© 2026 Anchor".
- **Icons:** Uses Google Material Symbols (Outlined) via font CSS includes.
- **Assets:** `screen.png` exists in the repo (likely a design or marketing asset); it is not currently referenced from `index.html`.

## Development and runtime commands

This project does not include any build system, package manager configuration, or automated tests. It is a plain static HTML file and can be opened directly in a browser or served via any static file server.

Common ways to work with this repo on macOS:

- **Preview the page directly in a browser:**
  - From the repo root: `open index.html`
- **Serve via a simple local HTTP server (helpful for testing form actions, relative paths, etc.):**
  - Using Python 3:
    - `python3 -m http.server 8000`
    - Then open `http://localhost:8000/` in a browser.

There are no standard `build`, `lint`, or `test` commands defined in this repository. If future work introduces a toolchain (e.g., a bundler, Tailwind CLI, or a test framework), update this `WARP.md` with the new commands and any relevant project structure changes.
