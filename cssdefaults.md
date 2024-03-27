# User Agent Stylesheet

The CSS defaults, often referred to as the "user agent stylesheet," is a set of default styles that web browsers apply to HTML elements in the absence of any author-defined styles. These defaults ensure that web content is legible and organized, even when no custom CSS is applied.

## Purpose of the Default Stylesheet

The default stylesheet serves several purposes:

1. **Consistency**: Provides a baseline level of consistency across different web browsers, though there are slight variations between browsers.
2. **Readability**: Ensures that content is readable out of the box, with sensible defaults for font sizes, margins, and so on.
3. **Usability**: Provides default styling for interactive elements (like form inputs) that is recognizable to users.

## How It Applies to Tags

Different HTML tags have default styles to reflect their semantic meanings and ensure they are distinguishable without custom styling. For example:

- **`<h1>` tags**: These are typically styled to be significantly larger than other text on the page, bold, and often have margins above and below to set them apart as main headings.
- **`<p>` tags**: Paragraph tags have default margins added above and below to separate blocks of text, making content easier to read. They usually don't have a different font size or weight from the body text.

## Examples

Here are some default styles you might see applied by the browser:

```css
/* Default styles for <h1> */
h1 {
    display: block;
    font-size: 2em; /* Typically 2 times the body font size */
    margin-top: 0.67em;
    margin-bottom: 0.67em;
    margin-left: 0;
    margin-right: 0;
    font-weight: bold;
}

/* Default styles for <p> */
p {
    display: block;
    margin-top: 1em; /* Creates space above each paragraph */
    margin-bottom: 1em; /* Creates space below each paragraph */
    margin-left: 0;
    margin-right: 0;
}
```

## Overriding Default Styles

Custom stylesheets can override these default styles. For example, if you want to change the look of all `<h1>` elements and `<p>` elements on your webpage, you might write:

```css
/* Custom styles */
h1 {
    color: darkblue; /* Changes the text color */
    font-size: 36px; /* Sets a specific font size */
    text-align: center; /* Centers the heading */
}

p {
    color: black; /* Sets the text color */
    font-size: 16px; /* Sets a specific font size */
    line-height: 1.5; /* Increases the space between lines for better readability */
}
```

By defining these styles in your stylesheet, you override the browser's default styles for these elements, giving your webpage a unique look and feel. It's worth noting that browsers' default styles can vary, so web designers often use CSS resets or normalization stylesheets to create a consistent baseline across browsers before applying custom styles.

# Chrome's Developer Tools to view CSS results

Viewing the resulting CSS for elements on a webpage using Chrome's Developer Tools allows you to inspect, modify, and debug the layout and styles of a webpage in real-time. Here's how you can do it:

## 3 Ways to Open Developer Tools:

1. **Using Keyboard Shortcuts**: Press `F12` on Windows to open DevTools directly.
2. **Right-Click Method**: Right-click on any element in the webpage you're interested in, and select `Inspect` from the context menu. This will open DevTools and highlight the HTML element you selected.
3. **Chrome Menu**: You can also access DevTools by clicking on the three dots in the upper-right corner of Chrome, then going to `More tools > Developer tools`.

## Viewing CSS Styles

Once DevTools is open, you can view and interact with the CSS in several ways:

- **Elements Panel**: The Elements panel is opened by default. It shows the HTML structure of the page. When you click on an HTML element in this panel, you'll see the CSS styles that apply to it in the right-hand side panels.

- **Styles Pane**: On the right side, when an element is selected, you'll find the Styles pane. This pane shows all CSS styles that are currently applied to the selected element, including styles from stylesheets, inline styles, and even styles that are inherited from parent elements. It's split into sections for matched CSS rules, inline styles, and inherited styles.

  - **Matched CSS Rules**: Shows the CSS rules that directly affect the selected element, listed in order of specificity. Styles crossed out have been overridden by more specific rules.
  - **Inherited Styles**: Shows CSS properties inherited from parent elements, which can be useful for understanding how text color, font styles, etc., are applied.

- **Computed Tab**: Next to the Styles tab, the Computed tab shows the computed style of the selected element. This view consolidates all CSS rules affecting the element and shows the final values after all the CSS has been applied, which is useful for debugging issues with styles not applying as expected.

## Modifying Styles (temporarily on your browser only) 

- **Editing Styles**: You can edit any CSS property directly in the Styles pane to see how changes would affect the layout and appearance of your page in real time. Just click on a property or value and start typing. Your changes will be applied immediately, but they're not permanent—they'll be lost once you reload the page.

- **Adding New Styles**: To add a new CSS rule to an element, click on the `+` icon in the top right corner of the Styles pane or just start typing a new rule at the start of an existing block. 

> [!TIP]
> Using Chrome's DevTools
> - **Filtering Styles**: In the Computed tab, you can filter computed styles by typing into the filter box, which is useful for quickly finding specific properties.
> - **Device Mode**: You can test how your styles look on different devices and screen sizes by clicking the 'Toggle device toolbar' button (icon of a small phone and tablet) to view your page in responsive mode.
> - **Color Picker**: When you click on a color value in the Styles pane, a color picker pops up, allowing you to visually select colors and see the changes in real time.

Using Chrome DevTools is an excellent way to learn about CSS, experiment with styles, and debug layout issues. The more you use it, the more proficient you'll become in understanding and manipulating web page styles.
