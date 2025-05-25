# Realtime Form Validation (Pure HTML & CSS)

> This project demonstrates form validation with immediate visual feedback, **including a password visibility toggle,** using only pure HTML & CSS, without any JavaScript.

## Overview

This project showcases a modern HTML form that provides realtime validation feedback and enhanced user experience features like a password visibility toggle. All validation logic, interactive elements, and styling are achieved using HTML5 input attributes and advanced CSS3 features, highlighting CSS's power for interactive UIs without JavaScript.

## Key Features

*   **No JavaScript:** 100% HTML and CSS.
*   **Immediate Visual Feedback:** Input fields change appearance (borders, icons) instantly based on validity.
*   **Password Visibility Toggle:** Show/hide password input using a pure CSS technique (a hidden checkbox manipulates the `text-security` property of a text input via sibling selectors, with labels styled as eye icons for toggling).
*   **Modern Styling:** Clean design with smooth transitions.
*   **HTML5 Validation:** Uses built-in attributes (`required`, `pattern`, `minlength`, `type`, etc.).
*   **Advanced CSS:**
    *   Native CSS Nesting.
    *   Pseudo-classes (`:valid`, `:invalid`, `:focus-within`, `:placeholder-shown`, experimental `:user-valid`/`:user-invalid`, `:checked`).
    *   Relational Pseudo-class (`:has()`) for scoping styles.
    *   Sibling Combinators (`~`, `+`) for icon display and password visibility logic.
    *   SVG icons via CSS `mask`.
    *   CSS `text-security` (via vendor prefixes) for password masking.

## How It Works

1.  **HTML5 Constraints:** The browser internally checks input values against attributes like `pattern` or `required`.
2.  **CSS Pseudo-classes:** Styles are applied based on states like `:valid`, `:invalid`, user interaction (`:focus`, `:placeholder-shown`), and checkbox state (`:checked`).
3.  **Sibling Selectors & Validation Icons:** CSS selectors (e.g., `input:valid ~ .validation-indicator`) show/hide appropriate SVG icons (`<check>`, `<x>`) placed next to the input fields. The icons are styled using CSS `mask`.
4.  **Password Visibility Toggle (CSS-Only):**
    *   The password field is an `input[type="text"]`.
    *   A visually hidden `input[type="checkbox"]` (`#css-password-reveal-toggle`) is placed before the password input and its toggle labels.
    *   Two `label` elements, associated with the checkbox, are styled as "show" (`eye.svg`) and "hide" (`eye-off.svg`) icons using CSS `mask`. Clicking these labels toggles the checkbox's state.
    *   CSS sibling combinators (`+`, `~`) and the `:checked` pseudo-class on the checkbox are used to:
        *   Conditionally apply `-webkit-text-security: disc;` (or `none`) to the password `input[type="text"]` field, effectively masking or revealing the characters.
        *   Toggle the visibility of the "show" and "hide" eye icons.
    *   The CSS rules for the password toggle are scoped within the `.input-container` using the `:has(#password)` pseudo-class for cleaner organization.

## Setup & Usage

1.  Clone or download this repository.
2.  Ensure you have `check.svg`, `cross.svg`, `eye.svg`, and `eye-off.svg` icon files in the same directory as `index.html` (or update paths in the CSS, for example, the `style.css` provided expects them in the same directory).
3.  Open `index.html` in a modern web browser.
4.  Interact with the form to see the validation and try the password visibility toggle.

**Note:** The `<form novalidate>` attribute disables default browser validation popups, allowing custom CSS feedback to dominate.

## Browser Support

*   Works best in modern browsers supporting native CSS Nesting, CSS `mask`, CSS `:has()`, HTML5 validation features, and the `-webkit-text-security` / `-moz-text-security` properties for the password toggle.
*   The password visibility toggle relies on `text-security` (prefixed) which has good support in WebKit/Blink-based browsers and Firefox.
*   Experimental pseudo-classes like `:user-valid`/`:user-invalid` offer progressive enhancement.
*   Graceful degradation: In browsers not supporting `text-security`, the password will always be visible (as it's a `type="text"` input). In browsers not supporting `:has()`, specific scoping for password toggle styles might not apply as intended but core functionality based on sibling selectors should remain if structured carefully.
