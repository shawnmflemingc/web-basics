# Using Telnet to see GET requests with a local Python web server

- **Telnet**: A network protocol used to provide a command-line interface for communicating with a remote device or server.
- **HTTP (Hypertext Transfer Protocol)**: The foundation of data communication for the World Wide Web, used for transmitting hypermedia documents, such as HTML.

### What You Learn

- How to start a basic web server using a Python command
- Submit a GET request manually by connecting to a web server
- See requests made from the Chrome web browser using the F12 Developer tools

To understand how HTTP works using Telnet and interacting with a local server created with Python's `http.server` module, follow these instructions:

## Install Telnet
First, ensure Telnet is installed on your computer by pressing Windows key then `R`, and type `telnet`. If it says command not found then you do not have it, and if it runs a program you do!

### Install Telnet on Windows 10:

1. **Open Control Panel**: You can do this by typing "Control Panel" in the search bar next to the Start menu and clicking on the Control Panel app.

2. **Programs and Features**: In the Control Panel, click on "Programs and Features". If your Control Panel view is set to "Category", you'll first click on "Programs", then "Programs and Features".

3. **Turn Windows features on or off**: On the left side of the "Programs and Features" window, you'll see an option for "Turn Windows features on or off". Click on this link.

4. **Enable Telnet**: A new window will open with a list of Windows features. Scroll down until you find "Telnet Client". Check the box next to "Telnet Client".

5. **Install**: Click "OK" to begin the installation. Windows will apply the changes and install the Telnet Client.

6. **Confirmation**: Once the installation is complete, you may need to click "Close" on the Windows features window. You should now have Telnet installed on your system.

### Install Telnet on Windows 11:

1. **Open Settings**: Press `Win + I` to open the Settings app, or you can right-click the Start button and select "Settings" from the menu.

2. **Apps**: In the Settings window, click on "Apps" from the sidebar.

3. **Optional Features**: Within the "Apps" section, click on "Optional Features".

4. **View Features**: Look for a button or link that says "View features" next to "Add an optional feature" and click on it.

5. **Search for Telnet**: In the "Add an optional feature" window, use the search box to search for "Telnet". You should see "Telnet Client" in the search results.

6. **Install Telnet**: Check the box next to "Telnet Client" and then click the "Next" or "Install" button to start the installation.

7. **Completion**: Once the installation process is complete, you can close the Settings app. Telnet Client should now be installed on your Windows 11 system.


## Python: Check that Python is working
Ensure Python is installed on your computer (it comes ArcGIS Pro). You can verify the installation using the Windows Start menu and typing Python, and it will show `Python Command Prompt`. 
You can also check for `python.exe`, which is the ArcGIS Pro default installation directory for it: `C:\Program Files\ArcGIS\Pro\bin\Python\envs\arcgispro-py3`. 

## Start Python's Simple HTTP Server
- Click on the `Python Command Prompt`.
- Navigate to the directory you want to serve using CD and type the path you want. For example, if you have a folder named `c:\gisworkspace\geom170` containing HTML files you'd like to serve, navigate to it using `cd c:\gisworkspace\geom170`.
- Start the server by running the following command:
    ```
    python3 -m http.server 8000
    ```
    This command tells Python to start its built-in HTTP server on TCP port 8000. You can use any available port, but 8000 is a common choice for testing. 

## Test Python's HTTP server is running using a web browser

 - Open a web browser (Chrome or Firefox) and try accessing your new webserver at `http://localhost:8000` to see if it lists the files in the directory where it was ran. If it does not, check your settings above. 

### Open Another Command Prompt Window
You'll need a separate window to connect to the server using Telnet because the first window is now occupied by the HTTP server.

### Run and Connect using Telnet
In the new terminal window, connect to your local server using Telnet by typing:
```
telnet localhost 8000
```
Here, `localhost` is the hostname for your local machine, and `8000` is the port where your server is running.

### Type your HTTP GET Request
Note: When you type you will NOT see those characters on screen in Telnet, but they are being sent to the web server. You also cannot use backspace to fix errors, so if you mistype start this step over!

After the connection is established, type your HTTP request. To request the homepage (or the directory listing if no index.html is present), type:
```
GET / HTTP/1.1
Host: localhost
```
Then, press Enter twice to finish the request.

### Observe the Response
You should see the HTTP response from your local server, including the status code, headers, and the content of the requested file or directory listing. You should also see the GET request on the python window. 

### GET specific files
To request a specific file from your web server, modify the GET request to include the path (directory) and filename:
```
GET /directory/filename.html HTTP/1.1
Host: localhost
```
The `Host: localhost` portion specifies the domain you are requesting. For example, if this was getting a file from Fleming College's website the line would read `Host: flemingcollege.ca`. The reason it is specified is because a single web server can host many websites, each with their own name.

### Close the Telnet Connection
To exit the Telnet session, type `^]` (Control key plus the right square bracket key), and then type `quit` at the Telnet prompt. Alternatively, you can close the terminal window.

## See how Chrome web browser makes GET requests

Forming a manual request using TELNET is nice to see it in action, but is not very easy. It is possible to see the GET requests made from a web browser. To view GET requests made by a webpage in Chrome's Developer Tools, follow these steps:

1. **Open Chrome and the Developer Tools**:
   - Open Chrome then open the Developer Tools by pressing `F12`, or right-clicking on the webpage and selecting "Inspect" from the context menu, or by using the keyboard shortcut `Ctrl+Shift+I`.

2. **Access Localhost Web Server**
   - Type in `http://localhost:8000` in the URL then press `Enter` to connect to your running python web server (or any other website).    

3. **Go to the Network Tab**:
   - Once the Developer Tools pane is open, locate and click on the "Network" tab. This tab shows all the network activity for the current webpage. Sometimes it is easier to change the settings to have the developer tools along the [bottom of your browser window](https://developer.chrome.com/docs/devtools/customize#placement).

4. **Initiate Network Activity**:
   - Opening the Developer Tools after the page might require a refresh of the page to see the network activity from the start. You can refresh the page by clicking the refresh button next to the address bar, pressing `F5` (hint, `SHIFT` + `F5` forces the web browser to retrieve a fresh copy of the web page into the browser, ignoring the cache made by previous requests).

5. **Review GET Requests**:
  - Hover over or click on a request to see more details on that individual request. The Name column shows the resource name or endpoint, while the Status column shows the HTTP status code (e.g., 200 for successful requests).

6. **Inspect Request Details**:
   - To see more details about a specific GET request, click on its name in the list. This will open a side panel with several tabs such as Headers, Preview, Response, etc.
   - The "Headers" tab shows all the request and response headers. Look for the "Request Method" in the request headers section to confirm it's a GET request.
   - The "Response" tab shows the actual data returned by the server in response to the GET request.

7. **Useful Features**:
   - **Preserve Log**: You can check the "Preserve log" checkbox to keep the network log across page loads, which is useful for tracking network activity during page navigation or redirects.
   - **Clear**: You can clear the current network log by clicking the "Clear" button (a circle with a line through it) before refreshing the page or initiating new network activity to focus on the new requests.

## Stop the Python HTTP Server
When you're finished experimenting, you can stop the HTTP server by going back to the first terminal window and pressing `Ctrl+C` to terminate the server process.

## Important Notes
- This exercise is excellent for understanding basic HTTP interactions. It's very rudimentary and serves educational purposes more than practical application.
- The Python HTTP server is intended for testing, development, or learning purposes and not for production use due to its basic nature and potential security implications.
- Remember, the Telnet protocol does not support encrypted communications (HTTPS/SSL), so it's not suitable for transmitting sensitive information, even in a local testing environment.

By setting up a simple local HTTP server and interacting with it via Telnet and Chrome, you gain a practical understanding of how web servers and HTTP requests work.
