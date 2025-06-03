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

## Complete ARIA Attributes Reference

ARIA (Accessible Rich Internet Applications) attributes provide semantic information to assistive technologies. ARIA is a set of roles and attributes that define ways to make web content and web applications more accessible to people with disabilities. Here's a comprehensive list organized by category:

### Widget Attributes
These attributes describe the state and properties of UI widgets:

| Attribute | Purpose | Example Usage | Values |
|-----------|---------|---------------|--------|
| `aria-autocomplete` | Indicates if text input triggers predictions | `<input aria-autocomplete="list">` | `none`, `inline`, `list`, `both` |
| `aria-checked` | Current checked state of checkboxes/radio buttons | `<input type="checkbox" aria-checked="true">` | `true`, `false`, `mixed` |
| `aria-disabled` | Indicates element is perceivable but not operable | `<button aria-disabled="true">Save</button>` | `true`, `false` |
| `aria-errormessage` | References element containing error message | `<input aria-errormessage="pwd-error">` | ID reference |
| `aria-expanded` | Whether collapsible element is expanded | `<button aria-expanded="false">Menu</button>` | `true`, `false` |
| `aria-haspopup` | Indicates element can trigger popup | `<button aria-haspopup="menu">Options</button>` | `false`, `true`, `menu`, `listbox`, `tree`, `grid`, `dialog` |
| `aria-hidden` | Whether element is exposed to accessibility API | `<span aria-hidden="true">👍</span>` | `true`, `false` |
| `aria-invalid` | Whether input value is valid | `<input aria-invalid="true">` | `false`, `true`, `grammar`, `spelling` |
| `aria-label` | Accessible name for element | `<button aria-label="Close dialog">×</button>` | String |
| `aria-level` | Hierarchical level of element | `<div role="heading" aria-level="3">` | Positive integer |
| `aria-modal` | Whether element is modal when displayed | `<div role="dialog" aria-modal="true">` | `true`, `false` |
| `aria-multiline` | Whether textbox accepts multiple lines | `<div role="textbox" aria-multiline="true">` | `true`, `false` |
| `aria-multiselectable` | Whether multiple items can be selected | `<ul role="listbox" aria-multiselectable="true">` | `true`, `false` |
| `aria-orientation` | Element's orientation | `<div role="slider" aria-orientation="vertical">` | `horizontal`, `vertical` |
| `aria-placeholder` | Short hint for expected input | `<input aria-placeholder="Enter your name">` | String |
| `aria-pressed` | Pressed state of toggle button | `<button aria-pressed="false">Bold</button>` | `true`, `false`, `mixed` |
| `aria-readonly` | Whether element is editable | `<input aria-readonly="true">` | `true`, `false` |
| `aria-required` | Whether input is required | `<input aria-required="true">` | `true`, `false` |
| `aria-selected` | Whether option is selected | `<li role="option" aria-selected="true">` | `true`, `false` |
| `aria-sort` | Sort direction of table column | `<th aria-sort="ascending">Name</th>` | `none`, `ascending`, `descending`, `other` |
| `aria-valuemax` | Maximum value for range | `<input type="range" aria-valuemax="100">` | Number |
| `aria-valuemin` | Minimum value for range | `<input type="range" aria-valuemin="0">` | Number |
| `aria-valuenow` | Current value for range | `<input type="range" aria-valuenow="50">` | Number |
| `aria-valuetext` | Human-readable value text | `<div role="slider" aria-valuetext="50%">` | String |

### Live Region Attributes
These attributes are used with ARIA live regions to announce dynamic content changes:

| Attribute | Purpose | Example Usage | Values |
|-----------|---------|---------------|--------|
| `aria-atomic` | Whether entire region should be announced | `<div aria-live="polite" aria-atomic="true">` | `true`, `false` |
| `aria-busy` | Whether element is being updated | `<div aria-busy="true">Loading...</div>` | `true`, `false` |
| `aria-live` | How live region updates are announced | `<div aria-live="assertive">Error occurred</div>` | `off`, `polite`, `assertive` |
| `aria-relevant` | What changes trigger announcements | `<div aria-live="polite" aria-relevant="additions text">` | `additions`, `removals`, `text`, `all` |

### Relationship Attributes
These attributes describe relationships between elements:

| Attribute | Purpose | Example Usage | Values |
|-----------|---------|---------------|--------|
| `aria-activedescendant` | Currently active descendant | `<div role="combobox" aria-activedescendant="option-2">` | ID reference |
| `aria-colcount` | Total number of columns | `<table aria-colcount="5">` | Positive integer |
| `aria-colindex` | Column index position | `<td aria-colindex="3">` | Positive integer |
| `aria-colindextext` | Human-readable column index | `<td aria-colindextext="Column C">` | String |
| `aria-colspan` | Number of columns spanned | `<td aria-colspan="2">` | Positive integer |
| `aria-controls` | Elements controlled by this element | `<button aria-controls="menu-list">Menu</button>` | Space-separated ID list |
| `aria-describedby` | Elements that describe this element | `<input aria-describedby="pwd-help">` | Space-separated ID list |
| `aria-description` | Description of the element | `<button aria-description="Saves your changes">Save</button>` | String |
| `aria-details` | Elements providing detailed information | `<img aria-details="chart-details">` | Space-separated ID list |
| `aria-flowto` | Next element in reading order | `<div aria-flowto="next-section">` | Space-separated ID list |
| `aria-labelledby` | Elements that label this element | `<input aria-labelledby="billing-header">` | Space-separated ID list |
| `aria-owns` | Child elements not in DOM hierarchy | `<div aria-owns="submenu">` | Space-separated ID list |
| `aria-posinset` | Position in set | `<li role="treeitem" aria-posinset="3">` | Positive integer |
| `aria-rowcount` | Total number of rows | `<table aria-rowcount="100">` | Positive integer |
| `aria-rowindex` | Row index position | `<tr aria-rowindex="5">` | Positive integer |
| `aria-rowindextext` | Human-readable row index | `<tr aria-rowindextext="Row 5 of 100">` | String |
| `aria-rowspan` | Number of rows spanned | `<td aria-rowspan="3">` | Positive integer |
| `aria-setsize` | Number of items in set | `<li role="treeitem" aria-setsize="10">` | Positive integer |

### Drag-and-Drop Attributes
These attributes are used for drag and drop operations:

| Attribute | Purpose | Example Usage | Values |
|-----------|---------|---------------|--------|
| `aria-dropeffect` | Functions performed when dropped | `<div aria-dropeffect="copy">Drop Zone</div>` | `none`, `copy`, `execute`, `link`, `move`, `popup` |
| `aria-grabbed` | Grabbed state in drag operation | `<div aria-grabbed="true">Draggable Item</div>` | `true`, `false` |

### Global ARIA Attributes
Many ARIA attributes are global, meaning they can be included on any element unless specifically disallowed. Most commonly used global attributes include:

| Attribute | Purpose | Example Usage |
|-----------|---------|---------------|
| `aria-current` | Current item in set | `<a href="/about" aria-current="page">About</a>` |
| `aria-keyshortcuts` | Keyboard shortcuts | `<button aria-keyshortcuts="Control+s">Save</button>` |
| `aria-roledescription` | Human-readable role description | `<div role="img" aria-roledescription="Temperature gauge">` |

### Braille-Specific Attributes
These newer attributes are designed for Braille display users:

| Attribute | Purpose | Example Usage |
|-----------|---------|---------------|
| `aria-braillelabel` | Braille-specific label | `<button aria-braillelabel="sv">Save</button>` |
| `aria-brailleroledescription` | Braille-specific role description | `<div aria-brailleroledescription="temp">` |

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

### Live Regions for Dynamic Content
```html
<!-- Status messages -->
<div id="status" aria-live="polite" aria-atomic="true"></div>

<!-- Error alerts -->
<div role="alert" aria-live="assertive">
  Error: Please fill in all required fields
</div>

<!-- Loading states -->
<div aria-live="polite" aria-busy="true">
  Loading your data...
</div>
```

### Complex Widgets
```html
<!-- Accessible data table -->
<table role="table" aria-label="Sales Data" aria-rowcount="1000">
  <thead>
    <tr role="row">
      <th role="columnheader" aria-sort="ascending">Product</th>
      <th role="columnheader" aria-sort="none">Sales</th>
      <th role="columnheader" aria-sort="none">Region</th>
    </tr>
  </thead>
  <tbody>
    <tr role="row" aria-rowindex="2">
      <td role="gridcell" aria-describedby="product-help">Widget A</td>
      <td role="gridcell">$1,250</td>
      <td role="gridcell">North</td>
    </tr>
  </tbody>
</table>

<!-- Accessible slider -->
<div role="slider" 
     aria-valuemin="0" 
     aria-valuemax="100" 
     aria-valuenow="25"
     aria-valuetext="25%"
     aria-label="Volume"
     tabindex="0">
  <div class="slider-thumb"></div>
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

// Update ARIA attributes dynamically
function toggleMenu() {
  const button = document.querySelector('[aria-controls="menu"]');
  const menu = document.getElementById('menu');
  const isExpanded = button.getAttribute('aria-expanded') === 'true';
  
  button.setAttribute('aria-expanded', !isExpanded);
  menu.hidden = isExpanded;
}
```

## Best Practices for ARIA Usage

1. **Use semantic HTML first** - Only use ARIA when native HTML doesn't provide the semantics you need
2. **Don't change semantics** - Avoid using ARIA to change what an element fundamentally is
3. **Ensure keyboard accessibility** - All interactive ARIA elements must be keyboard accessible
4. **Provide labels** - Interactive elements need accessible names via `aria-label` or `aria-labelledby`
5. **Test with screen readers** - The best way to verify ARIA implementation is testing with actual assistive technology
6. **Keep it simple** - Use the minimum ARIA necessary to convey meaning
7. **Update states dynamically** - Change ARIA states (like `aria-expanded`) as the UI changes
