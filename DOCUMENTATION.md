# Webflow Advanced Search with Autocomplete - Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [Setup](#setup)
3. [CMS Integration](#cms-integration)
4. [Keyboard Shortcuts and Navigation](#keyboard-shortcuts-and-navigation)
5. [Customization](#customization)
6. [Use Cases](#use-cases)
7. [Troubleshooting](#troubleshooting)

## Introduction

The Webflow Advanced Search with Autocomplete script enhances your Webflow site with powerful search capabilities. It provides real-time filtering of CMS items, keyboard navigation, and customizable search result actions.

## Setup

### Adding the Script

1. In your Webflow project, go to Project Settings > Custom Code.
2. In the "Footer Code" section, add the following script tag:

```html
<script src="https://cdn.jsdelivr.net/gh/shreyas-ws/autocomplete-search-with-cms@main/autocomplete-search-cms.min.js"></script>
```

### HTML Structure

Create the following structure in your Webflow designer:

1. Add a Form Block
2. Inside the Form Block, add a Text Input field
3. Add a Div block for search results
4. Add another Div block for the "no results" message

### Custom Attributes

Set these custom attributes in the Webflow designer:

- Form Block:
  - `tu-autosearch-element="search-form"`
  - `tu-autosearch-form-submit="false"` (optional, prevents form submission)
- Text Input: `tu-autosearch-element="search-input"`
- Search Results Div: `tu-autosearch-element="search-results"`
- No Results Div: `tu-autosearch-element="empty"`
- Each Collection List Item:
  - `tu-autosearch-element="search-result-item"`
  - `tu-autosearch-action="autocomplete"` or `tu-autosearch-action="open-link"`

Note on `tu-autosearch-form-submit`:

- If set to "false", it prevents the form from being submitted when the user presses Enter.
- If omitted or set to any other value, the form will submit normally.
- Use this when you want to prevent form submission and handle search entirely via JavaScript.

Example:

```html
<form tu-autosearch-element="search-form" tu-autosearch-form-submit="false">
  <input
    type="text"
    tu-autosearch-element="search-input"
    placeholder="Search..."
  />
  <div tu-autosearch-element="search-results">
    <!-- Search result items will be here -->
  </div>
  <div tu-autosearch-element="empty" style="display: none;">
    No results found.
  </div>
</form>
```

## CMS Integration

1. Create a CMS collection for your searchable items (if not already existing).
2. In the search results Div, add a Collection List and connect it to your CMS collection.
3. Design your Collection List Item to display search result information.
4. Add the required custom attributes to your Collection List Item.

## Keyboard Shortcuts and Navigation

The Advanced Search solution includes several keyboard shortcuts and navigation features to enhance user experience:

| Shortcut                  | Action                                     |
| ------------------------- | ------------------------------------------ |
| Ctrl + K (Cmd + K on Mac) | Focus the search input                     |
| ↓ (Down Arrow)            | Move focus to the next search result       |
| ↑ (Up Arrow)              | Move focus to the previous search result   |
| Enter                     | Select the currently focused search result |
| Esc (Escape)              | Clear the search input and hide results    |

Navigation Behavior:

- When search results are visible, using the arrow keys will cycle through the results.
- If you reach the end of the list with the down arrow, it will cycle back to the first item.
- If you reach the beginning of the list with the up arrow, it will cycle to the last item.
- The currently focused item will be scrolled into view if it's outside the visible area.

Note: Ensure that `tu-autosearch-form-submit="false"` is set on the form to prevent form submission when pressing Enter, allowing for proper keyboard navigation.

## Customization

### Styling

Style your search elements using Webflow's design tools:

- Set a max-height and enable vertical scrolling on the search results Div
- Create a "Focused" state for Collection List Items and style it accordingly

Example custom CSS:

```css
[tu-autosearch-element="search-results"] {
  max-height: 300px;
  overflow-y: auto;
}

[tu-autosearch-element="search-result-item"].is-focused {
  background-color: #f0f0f0;
}
```

### JavaScript Customization

To add custom JavaScript, use the "Before </body> tag" section in Project Settings > Custom Code.

## Use Cases

1. **Product Search**:

   - Use CMS collection for products
   - Display product image, name, and price in results
   - Use `tu-autosearch-action="open-link"` to link to product pages

2. **Blog Post Search**:

   - Filter existing blog post collection
   - Show post title, excerpt, and date in results
   - Use `tu-autosearch-action="autocomplete"` for instant filtering

3. **FAQ Search**:
   - Create a CMS collection for FAQ items
   - Display question text in search results
   - Use `tu-autosearch-action="autocomplete"` to filter FAQs in real-time

## Troubleshooting

- **Search not working**: Ensure all custom attributes are correctly set on your Webflow elements.
- **Form submitting unexpectedly**: Check if `tu-autosearch-form-submit="false"` is set on the form.
- **No results not showing**: Verify that the "empty" div is present and has the correct attribute.
- **Keyboard navigation not working**: Ensure the form has `tu-autosearch-form-submit="false"` set.
- **Script errors**: Check that the script is added correctly in the project's custom code section.
- **Styling issues**: Use Webflow's built-in styles wherever possible, and add custom CSS with high specificity.

For additional support or to report issues, please visit our support forum or GitHub issues page.
