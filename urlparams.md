# URL Parameters and Encoding
Introducing the concept of URL parameters and URL encoding can be learned by experimenting with a web search engine like Google. 

## Activity Overview:
You will use Google Search to observe how search queries are represented in the URL and then use an online URL encoding tool to understand how characters are encoded in URLs.

## Part 1: Exploring URL Parameters with Google Search

1. **Perform a Google Search**:
   - Open your web browser and go to [Google](https://www.google.com/).
   - Type in a simple search query, like `weather today`, and press Enter.

2. **Analyze the URL**:
   - Look at the URL in your browser's address bar. It should look something like this: `https://www.google.com/search?q=weather+today`.
   - Notice the `?q=weather+today` part. This is where the URL parameters begin. The `?` marks the start of the query parameters, and `q` is the name of a parameter that Google uses to represent the search query.

3. **Identify Parameters and Values**:
   - The parameter name (`q`) and its value (`weather today`) are separated by an `=` sign.
   - If you add more search parameters, they will be separated by `&`. For example, adding a language filter might look like `&lr=lang_en`.

4. **Modify the Search Query in the URL**:
   - In the address bar, change the search query after `q=` to something else, like `URL+parameters`, and press Enter. Observe how the search results change based on the modified URL.

## Understanding Special Characters in a URL

Remember the parts of a URL including the special characters that need to be there. First, a URL cannot have spaces. So the URL has these special characters to partition its parts. 

 - The `://` is between the scheme (protocol) and the domain
 - the `:` optionally specifies what port is going to be used
 - `/` are used in the path
 - `?` is the end of the file path and the beginning of the parameters
 - `=` separates the parameter key and value
 - `&` adds another key/value pair parameter
 - `#` denotes an anchor to jump to on the page

![URL Example](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-all.png)

These characters MUST not be modified and the HTTP protocol uses them to understand what to do, and what to pass on to the web page. The next part (URL Encoding) is all about protecting these special characters. For example, what if you want to use google to search on a term using one of these characters, or even all of them! 
In google, search for `:/?=& #` and see what it does in the URL. It replaces these characters with `%3A%2F%3F%3D%26+%23` to avoid confusing the URL. Basically it "encodes" each individual character as a 2-character Hexadecimal number (16-base counting) with a percent % before letting whatever needs it that the characters are encoded that way. 

## Part 2: URL Encoding Characters

In a URL, certain characters must be encoded because they have special meanings or are not allowed in URLs. Encoding these characters ensures the URL is correctly interpreted by web browsers and servers. Here’s a guide to which characters should be encoded in a URL and best practices for URL encoding:

### How to Encode

How to use Percent-Encoding:

Convert each byte value to a hexadecimal representation. For example, the ASCII value for a space is 20 in hexadecimal.
Prepend a % to the hexadecimal value. Thus, a space character is encoded as %20.

Here's a table of frequently used characters and their hexadecimal values in URL encoding. These are commonly needed when constructing or interpreting URLs:

| Character | HEX | Encoded Form |
|-----------|-------------|--------------|
| Space     | 20          | %20 or +         |
| # (Hash)  | 23          | %23          |
| % (Percent) | 25        | %25          |
| & (Ampersand) | 26      | %26          |
| + (Plus)  | 2B          | %2B          |
| , (Comma) | 2C          | %2C          |
| / (Slash) | 2F          | %2F          |
| : (Colon) | 3A          | %3A          |
| = (Equals) | 3D         | %3D          |
| ? (Question Mark) | 3F  | %3F          |
| \| (Vertical Bar) | 7C  | %7C          |

These are just a few of the Hex codes. For a full list of Hexadecimal (HEX) codes, see the column Hx in the table [ASCII table](https://www.asciitable.com/)

**Notes** technically ALL characters can be encoded. 

- The letter `A` can be encoded as `%41`, but there is no need to encode alpha-numeric characters (letters and numbers) because they do not have special meaning to the parts of a URL.
- Do not encode special characters when they do have meaning in a URL. For example the beginning of URL parameters is indicated by a `?` (question mark). If that `?` character was encoded as `%3F` the `?` would no longer indicate parmeters start and the URL would be broken. 
- The most common place for URL encoding to be required is in the value portion of parameters, so if trying to encode something that is not a parameter value, be sure it is necessary.
- There would never be a case to encode any characters as part of a domain name. 

### Characters to be Encoded:

1. **Reserved Characters**: These characters have special meanings in URLs and must be encoded when used in a different context:
   - `;`, `/`, `?`, `:`, `@`, `=`, `&`, `#`
   - For example, `?` is used to signify the start of a query string, so it must be encoded if it's part of a query parameter.

2. **Unsafe Characters**: These characters may be misunderstood within URLs for various reasons and should be encoded:
   - Space (` `) is encoded as `%20` or `+`. Yes, it has two options! Don't make the mistake of encoding the +, as that IS the space!
   - Double quotes (`"`), `<`, `>`, `[`, `]`, `\`, `^`, `` ` ``, `{`, `}`, `|`, and `%` itself.

3. **Non-ASCII Characters**: Characters outside the ASCII set, including characters from other languages and special symbols, must be encoded. They are first converted to bytes using a character encoding like UTF-8, then each byte is percent-encoded.

### Characters Not Requiring Encoding:

- Alpha-numeric characters (`A-Z`, `a-z`, `0-9`) are safe and do not require encoding.
- A few special characters are considered safe and do not require encoding: `-`, `_`, `.`, `!`, `~`, `*`, `'`, `(`, `)`.

### Best Practice Guide:

1. **Always Encode Reserved and Unsafe Characters**: When constructing URLs, ensure that reserved characters used outside their special context and all unsafe characters are percent-encoded.

2. **Normalize URLs Before Encoding**: If you're programmatically constructing URLs, normalize them first. This includes removing unnecessary slashes, converting the domain to lowercase, and removing default ports.

3. **Be Consistent with Encoding**: Be consistent in how you encode URLs within your application to avoid confusion and potential errors.

4. **Test Encoded URLs**: Test your encoded URLs to ensure they resolve to the correct resource. Special attention should be paid to complex URLs with many parameters or those using non-ASCII characters.

5. **`%20` and `+` both represent `SPACE`**: If using `+` to encode spaces, don't make the mistake to encode the + itself as %2B. 

Following these guidelines will help ensure that your URLs are correctly formatted and interpreted by web browsers and servers, enhancing the reliability and usability of your web applications.

