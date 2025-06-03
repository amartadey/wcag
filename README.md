# WCAG Web Content Accessibility Guidelines - Simple Reference

## Overview
WCAG (Web Content Accessibility Guidelines) are organized around 4 main principles, with 13 guidelines total. Each guideline has multiple success criteria at different levels (A, AA, AAA).

| Principle | Guideline | What It Means | Simple Examples | Code Examples |
|-----------|-----------|---------------|-----------------|---------------|
| **1. PERCEIVABLE** | | | | |
| | **1.1 Text Alternatives** | All non-text content needs text descriptions | Add alt text to images, captions for videos, labels for charts | `<img src="cat.jpg" alt="Orange tabby cat sleeping on windowsill">` <br> `<img src="chart.png" alt="Sales increased 25% from Jan to Mar">` |
| | **1.2 Time-based Media** | Videos and audio need alternatives | Provide captions for videos, transcripts for podcasts, audio descriptions | `<video controls>` <br> `  <source src="video.mp4" type="video/mp4">` <br> `  <track kind="captions" src="captions.vtt" srclang="en" label="English">` <br> `</video>` |
| | **1.3 Adaptable** | Content can be presented in different ways without losing meaning | Use proper headings (H1, H2, H3), structure tables correctly, don't rely only on color | `<h1>Main Title</h1>` <br> `<h2>Section Title</h2>` <br> `<h3>Subsection</h3>` <br><br> `<table>` <br> `  <th scope="col">Name</th>` <br> `  <th scope="col">Age</th>` <br> `</table>` |
| | **1.4 Distinguishable** | Make it easy for users to see and hear content | Good color contrast, text can be resized, don't rely only on color | `/* Good contrast */` <br> `.text { color: #333; background: #fff; }` <br><br> `/* Don't do this */` <br> `.error { color: red; }` <br> `/* Do this instead */` <br> `.error { color: red; }` <br> `.error::before { content: "⚠ "; }` |
| **2. OPERABLE** | | | | |
| | **2.1 Keyboard Accessible** | All functions work with keyboard only | Can tab through all buttons/links, no mouse-only features | `<button type="button" onclick="showMenu()">Menu</button>` <br><br> `<div tabindex="0" role="button" onkeydown="handleKeyPress(event)" onclick="doAction()">Custom Button</div>` |
| | **2.2 Enough Time** | Users have enough time to read and use content | No auto-refreshing pages, give time extensions, pause/stop moving content | `<!-- Don't auto-refresh -->` <br> `<!-- <meta http-equiv="refresh" content="30"> -->` <br><br> `<button onclick="pauseCarousel()">Pause Slideshow</button>` |
| | **2.3 Seizures and Physical Reactions** | Don't cause seizures or physical reactions | No flashing content more than 3 times per second | `/* Avoid rapid flashing */` <br> `@keyframes flash {` <br> `  0%, 100% { opacity: 1; }` <br> `  50% { opacity: 0.5; }` <br> `}` <br> `/* Animation duration should be > 0.33s */` <br> `.flash { animation: flash 1s infinite; }` |
| | **2.4 Navigable** | Help users navigate and find content | Skip links, page titles, focus indicators, breadcrumbs | `<a href="#main" class="skip-link">Skip to main content</a>` <br><br> `<title>Contact Us - Acme Corp</title>` <br><br> `button:focus { outline: 2px solid blue; }` |
| | **2.5 Input Modalities** | Make it easier to operate through various inputs | Works with touch, voice, other input methods beyond keyboard/mouse | `<button style="min-height: 44px; min-width: 44px;">Touch-friendly button</button>` <br><br> `<input type="text" name="search" aria-label="Search products">` |
| **3. UNDERSTANDABLE** | | | | |
| | **3.1 Readable** | Make text readable and understandable | Clear language, define unusual words, set page language | `<html lang="en">` <br><br> `<abbr title="World Wide Web">WWW</abbr>` <br><br> `<p>The CEO will give a presentation about our <dfn>key performance indicators</dfn> (metrics we use to measure success).</p>` |
| | **3.2 Predictable** | Web pages work in predictable ways | Navigation stays consistent, forms don't auto-submit, changes are expected | `<!-- Consistent navigation -->` <br> `<nav>` <br> `  <a href="/">Home</a>` <br> `  <a href="/about">About</a>` <br> `  <a href="/contact">Contact</a>` <br> `</nav>` <br><br> `<!-- Don't auto-submit forms -->` <br> `<select onchange="handleChange()" name="country">` |
| | **3.3 Input Assistance** | Help users avoid and correct mistakes | Clear error messages, form labels, suggestions for fixing errors | `<label for="email">Email Address *</label>` <br> `<input type="email" id="email" required aria-describedby="email-error">` <br> `<div id="email-error" class="error">Please enter a valid email address like user@example.com</div>` |
| **4. ROBUST** | | | | |
| | **4.1 Compatible** | Content works with assistive technologies | Valid HTML code, proper ARIA labels, works with screen readers | `<button aria-expanded="false" aria-controls="menu" onclick="toggleMenu()">Menu</button>` <br> `<ul id="menu" hidden>...</ul>` <br><br> `<div role="alert" aria-live="polite">Form saved successfully</div>` |

## Conformance Levels

| Level | Description | When to Use |
|-------|-------------|-------------|
| **A** | Minimum level | Basic accessibility - addresses major barriers |
| **AA** | Standard level | **Recommended target** - good accessibility for most users |
| **AAA** | Highest level | Enhanced accessibility - often not required for entire sites |

## Quick Checklist for Common Issues

| Check This | Why It Matters |
|------------|----------------|
| ✓ All images have alt text | Screen readers can describe images to blind users |
| ✓ Videos have captions | Deaf users can understand video content |
| ✓ Text contrast ratio is at least 4.5:1 | Users with low vision can read text clearly |
| ✓ All buttons/links work with Tab key | Keyboard-only users can navigate your site |
| ✓ Forms have clear labels | Users know what information to enter |
| ✓ Page has proper heading structure (H1→H2→H3) | Screen readers can navigate by headings |
| ✓ Error messages are clear and helpful | Users understand what went wrong and how to fix it |
| ✓ No content flashes more than 3 times per second | Prevents seizures in susceptible users |

## Common Code Patterns for Accessibility

### Form Accessibility
```html
<!-- Proper form labeling -->
<form>
  <label for="name">Full Name *</label>
  <input type="text" id="name" required aria-describedby="name-help">
  <div id="name-help">Enter your first and last name</div>
  
  <fieldset>
    <legend>Preferred Contact Method</legend>
    <input type="radio" id="email" name="contact" value="email">
    <label for="email">Email</label>
    <input type="radio" id="phone" name="contact" value="phone">
    <label for="phone">Phone</label>
  </fieldset>
</form>
```

### Interactive Elements
```html
<!-- Dropdown menu -->
<button aria-expanded="false" aria-haspopup="true" onclick="toggleDropdown()">
  Settings
</button>
<ul role="menu" hidden>
  <li role="menuitem"><a href="/profile">Profile</a></li>
  <li role="menuitem"><a href="/settings">Settings</a></li>
</ul>

<!-- Modal dialog -->
<button onclick="openModal()">Open Dialog</button>
<div role="dialog" aria-labelledby="modal-title" aria-modal="true" hidden>
  <h2 id="modal-title">Confirm Action</h2>
  <p>Are you sure you want to delete this item?</p>
  <button onclick="closeModal()">Cancel</button>
  <button onclick="confirmDelete()">Delete</button>
</div>
```

### Focus Management
```css
/* Visible focus indicators */
button:focus,
a:focus,
input:focus {
  outline: 2px solid #0066cc;
  outline-offset: 2px;
}

/* Skip link styling */
.skip-link {
  position: absolute;
  top: -40px;
  left: 6px;
  background: #000;
  color: #fff;
  padding: 8px;
  text-decoration: none;
}

.skip-link:focus {
  top: 6px;
}
```

### JavaScript for Keyboard Navigation
```javascript
// Handle keyboard events for custom interactive elements
function handleKeyPress(event) {
  if (event.key === 'Enter' || event.key === ' ') {
    event.preventDefault();
    // Trigger the action
    doAction();
  }
}

// Manage focus for single-page applications
function announceLiveRegion(message) {
  const liveRegion = document.getElementById('live-region');
  liveRegion.textContent = message;
}
```
