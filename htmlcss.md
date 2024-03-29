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

> [!NOTE]
> Best practice for HTML tags are to always use lowercase given they are not case sensitive.

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

> [!WARNING]
> CSS is generally Case Sensitive!

## Combining HTML and CSS

There are three ways to combine HTML and CSS together. 

1. Internal CSS
2. External CSS
3. Inline CSS

> [!TIP]
> It is a best practice to keep all your CSS contained together using either External or Internal (but not both together) and to avoid Inline CSS. 

### Add a STYLE section for Internal CSS

In your HTML document's `<head>` section, add a `<style>` section to contain the CSS selectors and declarations for that page. 

```html
<!DOCTYPE html>
<html>
<head>
<!--below is the start of the CSS internal section-->
<style>
# This section uses CSS syntax only, no HTML!
body {
  background-color: linen;
}
h1 {
  color: maroon;
  margin-left: 40px;
}
</style>
<!--Above is the end of the style section and now the document returns to HTML-->
</head>
<body>
<h1>My document is here.</h1>
</body>
</html>
```

### Link to external CSS

> [!TIP]
> External CSS files are great to share the same CSS among multiple pages and is a best practice to use. 

To link an external CSS file to an HTML document, you use the `<link>` tag inside the `<head>` section of your HTML file naming your file with the `.css` extension:

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

Here is what the styles.css file would look like:

```css
# This file uses CSS syntax only, never put HTML in it!
body {
  background-color: linen;
}
h1 {
  color: maroon;
  margin-left: 40px;
}
```
This link tells the browser to fetch and apply the styles from `styles.css` to the HTML document. Never include the `<style>` HTML tag in this external document. 

Experimentation and practice are key to learning HTML and CSS, so try creating simple pages and gradually incorporate more complex structures and styles using the https://w3schools.com/html and https://w3schools.css websites.
