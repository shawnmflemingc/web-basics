# HTML and CSS

HTML (HyperText Markup Language) and CSS (Cascading Style Sheets) are the foundation of web development. HTML provides the structure of the page, while CSS specifies the page's layout, colors, and fonts. Together, they allow you to create visually engaging and structured web pages.

## HTML Basics

HTML uses **tags** to mark up the content, telling the web browser how to display it. These tags are enclosed in angle brackets, like `<tagname>content</tagname>`. While HTML is not case sensitive, it is a best practice to have it in lowercase. Here are some basic HTML elements:

- **`<!DOCTYPE html>`**: Declares the document type and HTML version. It is always at the top of the HTML document and has no ending tag `</tagname>` since this really isn't HTML. 
- **`<html>`**: The root element that contains all other HTML elements. This will be right after the document type (above) and will also be the last tag to end `</html>`
- **`<head>`**: Contains metadata and links to external resources like CSS files.
- **`<title>`**: Sets the title of the web page, shown in the browser's title bar or tab and is contained within the `<head>` section.
- **`<body>`**: Contains the content of the web page, such as text, images, and other media.
- **`<h1>`, `<h2>`, ..., `<h6>`**: Header tags, with `<h1>` being the highest level, `<h6>` being the lowest.
- **`<p>`**: Defines a paragraph.
- **`<a href="URL">`**: Creates a hyperlink to another HTML page or document to download.
- **`<img src="imageURL" alt="text">`**: Embeds an image.

## CSS Basics

CSS is used to style the HTML content. It can be included in three ways: inline, internal, or external. Most professional websites use external CSS files to keep content and design separate.

CSS syntax consists of **selectors** and **declarations**. The selector points to the HTML element you want to style, and the declaration block contains one or more declarations separated by semicolons. Each declaration includes a property and a value, separated by a colon.

```css
selector {
  property: value;
}
```

For example:

```css
body {
  background-color: lightblue;
}

h1 {
  color: navy;
  margin-left: 20px;
}
```

This CSS will set the background color of the entire page to light blue and give all `<h1>` elements a navy color with a margin on the left.

## Combining HTML and CSS

To link an external CSS file to an HTML document, you use the `<link>` tag inside the `<head>` section of your HTML file:

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

This link tells the browser to fetch and apply the styles from `styles.css` to the HTML document.

By mastering HTML and CSS, you'll be able to create and style a wide range of web pages. Experimentation and practice are key, so try creating simple pages and gradually incorporate more complex structures and styles using the https://w3schools.com/html and https://w3schools.css websites.
