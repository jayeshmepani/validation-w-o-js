# Realtime Form Validation (Pure HTML & CSS)

> This project demonstrates form validation with immediate visual feedback, using only pure HTML & CSS, without any JavaScript.

## Overview

This project showcases a modern HTML form that provides realtime validation feedback. All validation logic and styling are achieved using HTML5 input attributes and advanced CSS3 features, highlighting CSS's power for interactive UIs without JavaScript.

## Key Features

*   **No JavaScript:** 100% HTML and CSS.
*   **Immediate Visual Feedback:** Input fields change appearance (borders, icons) instantly based on validity.
*   **Modern Styling:** Clean design with smooth transitions.
*   **HTML5 Validation:** Uses built-in attributes (`required`, `pattern`, `minlength`, `type`, etc.).
*   **Advanced CSS:**
    *   Native CSS Nesting.
    *   Pseudo-classes (`:valid`, `:invalid`, `:focus-within`, `:placeholder-shown`, experimental `:user-valid`/`:user-invalid`).
    *   Sibling Combinator (`~`) for icon display.
    *   SVG icons via CSS `mask`.

## How It Works

1.  **HTML5 Constraints:** The browser internally checks input values against attributes like `pattern` or `required`.
2.  **CSS Pseudo-classes:** Styles are applied based on states like `:valid`, `:invalid`, and user interaction (`:focus`, `:placeholder-shown`).
3.  **Sibling Selectors & Icons:** CSS selectors (e.g., `input:valid ~ .validation-indicator`) show/hide appropriate SVG icons (`<check>`, `<x>`) placed next to the input fields. The icons are styled using CSS `mask`.

## Setup & Usage

1.  Clone or download this repository.
2.  Ensure you have `check.svg` and `cross.svg` icon files in the same directory as `index.html` (or update paths in the CSS).
3.  Open `index.html` in a modern web browser.
4.  Interact with the form to see the validation.

**Note:** The `<form novalidate>` attribute disables default browser validation popups, allowing custom CSS feedback to dominate.

## Browser Support

*   Works best in modern browsers supporting native CSS Nesting, CSS `mask`, and HTML5 validation features.
*   Experimental pseudo-classes like `:user-valid`/`:user-invalid` offer progressive enhancement.
