# Realtime Form Validation (Pure HTML & CSS Focus)

> This project demonstrates modern form validation with immediate visual feedback. The core validation styling and a clever CSS-only password visibility toggle are achieved using pure HTML & CSS, without JavaScript. For comparison and completeness, a standard JavaScript-enhanced password toggle is also included.

## Overview

This project showcases an HTML form that provides realtime validation feedback and enhanced user experience features. The primary focus is on leveraging HTML5 input attributes and advanced CSS3 features to achieve interactive UI elements and validation logic, highlighting CSS's power for such tasks.

The `index.html` file includes a `<note>` section that explicitly details the two different password field implementations:
1.  A **CSS-only password toggle** using `type="text"` and CSS `text-security`.
2.  A **JavaScript-enhanced password toggle** using `type="password"` and JS to change the input type (the standard, recommended approach).

This dual approach allows for a practical demonstration of pure CSS capabilities alongside a comparison with common JavaScript solutions. The `novalidate` attribute is used on the `<form>` to disable default browser validation popups, allowing the custom CSS feedback to take precedence.

## Key Features

*   **Rich HTML5 Validation:** Utilizes built-in attributes like `required`, `pattern`, `minlength`, `maxlength`, `min`, `max`, and input `type`s (e.g., `email`, `number`, `tel`, `url`).
*   **Immediate Visual Feedback:** Input fields dynamically change appearance (borders, background, icons) based on their validation status (`:valid`, `:invalid`) and user interaction (`:focus`, `:placeholder-shown`).
*   **Custom Validation Indicators:** Uses custom HTML elements (`<check>`, `<x>`) styled with SVG icons via CSS `mask` to show success or error states.
*   **CSS-Only Password Visibility Toggle:** The first password field demonstrates a technique to show/hide password characters using a hidden checkbox, CSS sibling combinators (`~`, `+`), the `:checked` pseudo-class, and the non-standard `-webkit-text-security` / `-moz-text-security` CSS properties.
*   **JavaScript-Enhanced Password Toggle:** The second password field provides a standard implementation using `type="password"` and a small JavaScript snippet to toggle visibility, ensuring broader compatibility and accessibility.
*   **Modern Styling:** Clean, responsive design with smooth transitions and CSS Variables.
*   **Advanced CSS Utilized:**
    *   Native CSS Nesting for organized stylesheets.
    *   Relational Pseudo-class (`:has()`) for more targeted styling (e.g., scoping password toggle styles).
    *   Interaction Pseudo-classes (`:focus-within`, `:placeholder-shown`).
    *   Experimental User Action Pseudo-classes (`:user-valid`, `:user-invalid`) for progressive enhancement, styling inputs after user interaction.
    *   SVG icons integrated via CSS `mask` property.
*   **No JavaScript for Core Validation:** All form field validation logic and visual feedback (excluding the second password toggle) are pure HTML and CSS.

## How It Works

1.  **HTML5 Constraint Validation:** The browser internally validates input values against HTML attributes (`pattern`, `required`, `type`, etc.) and sets `:valid` or `:invalid` pseudo-classes on the input elements.
2.  **CSS Pseudo-classes for Styling:**
    *   `:valid` and `:invalid` are used to style inputs based on their current validity.
    *   `:placeholder-shown` is used to determine if an input has content or is empty (showing placeholder), often preventing premature validation messages.
    *   `:focus` and `:focus-within` enhance UX during interaction.
    *   Experimental `:user-valid` and `:user-invalid` (where supported) provide feedback that feels more "on interaction" rather than "on load for pre-filled invalid fields."
3.  **Sibling Selectors & Validation Icons:**
    *   `<span class="validation-indicator">` elements containing custom `<check>` (for valid) and `<x>` (for invalid) elements are placed next to inputs.
    *   CSS sibling combinators (e.g., `input:valid:not(:placeholder-shown) ~ .validation-indicator[valid]`) control the opacity and transform of these icons, making them appear when an input is validated (and not empty).
    *   The `<check>` and `<x>` elements are styled using CSS `mask` with `check.svg` and `cross.svg` files.
4.  **CSS-Only Password Visibility Toggle (First Password Field - `#password`):**
    *   The password input is `type="text"`.
    *   A visually hidden `input[type="checkbox"]` (`#css-password-reveal-toggle`) is placed before the text input and its toggle labels.
    *   Two `<label>` elements, associated with the checkbox, are styled as "show" (`eye.svg`) and "hide" (`eye-off.svg`) icons using CSS `mask`. Clicking these labels toggles the checkbox's state.
    *   CSS sibling combinators (`+`, `~`) and the `:checked` pseudo-class on the checkbox are used to:
        *   Conditionally apply `-webkit-text-security: disc;` (or `none`) to the password `input[type="text"]` field, effectively masking or revealing the characters. Placeholder text remains visible by resetting its `text-security` property.
        *   Toggle the visibility of the "show" and "hide" eye icon labels.
    *   These specific styles are neatly scoped using `.input-container:has(#password)`.
5.  **JavaScript-Enhanced Password Visibility Toggle (Second Password Field - `#password-js`):**
    *   This field uses the standard `input[type="password"]`.
    *   A small JavaScript snippet (included in `index.html`) listens for clicks on "show" (`#js-eye`) and "hide" (`#js-eye-off`) icon `<span>` elements.
    *   It toggles the `type` attribute of the password input between `password` and `text` and updates the visibility of the eye icons accordingly. This is the generally recommended method for password visibility toggles.

## Setup & Usage

1.  Clone or download this repository/code.
2.  Ensure you have the following SVG icon files in the same directory as `index.html` and `style.css` (or update paths in `style.css` accordingly):
    *   `check.svg`
    *   `cross.svg`
    *   `eye.svg`
    *   `eye-off.svg`
3.  Open `index.html` in a modern web browser.
4.  Interact with the form fields to observe the realtime validation feedback and test both password visibility toggles.

## Browser Support

*   **Core Validation & Styling:** Works best in modern browsers supporting HTML5 validation, CSS Nesting, CSS `:has()`, CSS `mask`, and advanced CSS pseudo-classes.
*   **CSS-Only Password Toggle:** Relies on `-webkit-text-security` (Chrome, Safari, Edge, Opera) and `-moz-text-security` (Firefox). In browsers not supporting `text-security`, the password in this field will always be visible as it's a `type="text"` input.
*   **JavaScript-Enhanced Password Toggle:** Works in all modern browsers that support basic JavaScript DOM manipulation.
*   **Experimental Features:** Pseudo-classes like `:user-valid`/`:user-invalid` are experimental and provide progressive enhancement where supported.
*   **Graceful Degradation:** Basic HTML5 validation will still function in older browsers, though custom styling might not be fully applied. For instance, if CSS Nesting or `:has()` is not supported, some styles might not apply as intended, but the form should remain largely functional.

This project serves as an excellent learning resource for understanding advanced CSS capabilities in form handling and UI interactions.
