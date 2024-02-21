# Using Telnet to see GET requests against the Python local web server

- **Telnet**: A network protocol used to provide a command-line interface for communicating with a remote device or server.
- **HTTP (Hypertext Transfer Protocol)**: The foundation of data communication for the World Wide Web, used for transmitting hypermedia documents, such as HTML.

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

### Start a Simple HTTP Server
- Click on the `Python Command Prompt`.
- Navigate to the directory you want to serve using CD and type the path you want. For example, if you have a folder named `c:\gisworkspace\geom170` containing HTML files you'd like to serve, navigate to it using `cd c:\gisworkspace\geom170`.
- Start the server by running the following command:
    ```
    python3 -m http.server 8000
    ```
    This command tells Python to start its built-in HTTP server on TCP port 8000. You can use any available port, but 8000 is a common choice for testing. 

### Test using a web browser

 - Open a web browser and try accessing your new webserver at `http://localhost:8000` to see if it lists the files in the directory where it was ran. If it does not, check your settings above. 

### Start Telnet: Open Another Command Prompt Window
You'll need a separate window to connect to the server using Telnet because the first window is now occupied by the HTTP server.

### Step 4: Connect Using Telnet
In the new terminal window, connect to your local server using Telnet by typing:
```
telnet localhost 8000
```
Here, `localhost` is the hostname for your local machine, and `8000` is the port where your server is running.

### Step 5: Make an HTTP Request
Note: When you type you will NOT see those characters on screen in Telnet, but they are being sent to the web server. You also cannot use backspace to fix errors, so if you mistype start this step over!

After the connection is established, type your HTTP request. To request the homepage (or the directory listing if no index.html is present), type:
```
GET / HTTP/1.1
Host: localhost
```
Then, press Enter twice to finish the request.

### Step 6: Observe the Response
You should see the HTTP response from your local server, including the status code, headers, and the content of the requested file or directory listing.

### Step 7: Close the Connection
To exit the Telnet session, type `^]` (Control key plus the right square bracket key), and then type `quit` at the Telnet prompt. Alternatively, you can close the terminal window.

### Step 8: Stop the HTTP Server
When you're finished experimenting, you can stop the HTTP server by going back to the first terminal window and pressing `Ctrl+C` to terminate the server process.

### Important Notes
- This exercise is excellent for understanding basic HTTP interactions. It's very rudimentary and serves educational purposes more than practical application.
- The Python HTTP server is intended for testing, development, or learning purposes and not for production use due to its basic nature and potential security implications.
- Remember, the Telnet protocol does not support encrypted communications (HTTPS/SSL), so it's not suitable for transmitting sensitive information, even in a local testing environment.

By setting up a simple local HTTP server and interacting with it via Telnet, you gain a practical understanding of how web servers and HTTP requests work.
