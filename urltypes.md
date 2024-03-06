# Relative, Absolute and no paths in URLs

URLs (Uniform Resource Locators) are used to specify addresses on the Internet. They can vary in form, indicating different types of paths or even no path at all. Understanding the differences between having no path, a relative path, and a full absolute path is crucial for web development and navigation.

## No Path

A URL with no path simply points to the root of a website. It typically consists of a scheme (like `http`, `https`), followed by a colon, two forward slashes, and then the domain name. For example:

```
https://www.example.com
```

In this case, the URL directs the browser to the main entry point of the website, usually the home page. There's no specific path or resource specified after the domain name. When this is used the web server decides what document to show, which usually is a file named `index.html` or `default.htm`. 

## Relative Path

Relative paths in URLs are used to navigate between directories and resources within the same website without specifying the domain name and protocol. If you can, always use relative paths if staying on the same website so the website remains "portable", where the domain name may change. Here are more examples to illustrate various uses of relative paths, particularly for changing directories:

### 1. Same Directory

If you're linking to a file in the same directory as the current document, you just need to specify the file name.

- Current URL: `https://www.example.com/folder/page1.html`
- Relative path to another file in the same folder: `page2.html`
- Resulting URL: `https://www.example.com/folder/page2.html`

### 2. Subdirectory

To link to a file in a subdirectory of the current directory, include the subdirectory name followed by the file name.

- Current URL: `https://www.example.com/folder/page.html`
- Relative path to a file in a subdirectory: `subfolder/item.html`
- Resulting URL: `https://www.example.com/folder/subfolder/item.html`

### 3. Parent Directory

To link to a file in the parent directory of the current directory, use `..` to navigate up one level.

- Current URL: `https://www.example.com/folder/subfolder/page.html`
- Relative path to a file in the parent directory: `../parent-page.html`
- Resulting URL: `https://www.example.com/folder/parent-page.html`

### 4. Root Directory

To link to a file at the root of the domain, start the relative path with a `/`. This is technically a root-relative path rather than a purely relative one.

- Current URL: `https://www.example.com/folder/page.html`
- Relative path to a file in the root directory: `/root-item.html`
- Resulting URL: `https://www.example.com/root-item.html`

### 5. Navigating Multiple Levels

To navigate up multiple levels in the directory structure, chain `..` together with `/`.

- Current URL: `https://www.example.com/folder1/folder2/folder3/page.html`
- Relative path to go up two levels and into another directory: `../../folder4/item.html`
- Resulting URL: `https://www.example.com/folder1/folder4/item.html`

### 6. Current Directory

To specify a file or a subdirectory in the current directory without moving up or down the directory tree, you can start with `./`, though this is often optional.

- Current URL: `https://www.example.com/folder/page.html`
- Relative path to a file in the current directory: `./another-page.html` (or simply `another-page.html`)
- Resulting URL: `https://www.example.com/folder/another-page.html`

Understanding how to use relative paths efficiently can make your web development projects more flexible and easier to maintain, especially when moving or restructuring content within the same domain.

## Full Absolute Path

A full absolute path, or an absolute URL, includes everything: the scheme, the domain, and the complete path to the resource. 

For example:

```
https://www.example.com/folder1/subfolder/item.html
```

This URL is absolute because it provides the entire path from the top-level domain to the specific resource, `item.html`. Absolute paths are clear and unambiguous, making them necessary when linking to resources on different websites or when a clear reference is needed regardless of the current page's context.

In summary, URLs with no path point to the root of a website, relative paths specify a resource using the current URL as the base, and full absolute paths provide the complete address to a resource, including the scheme and domain name. Understanding these differences is crucial for creating effective links in HTML, CSS and other resources.
