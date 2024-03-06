# Understanding HTTP/HTTPS and TCP Ports

HTTP (HyperText Transfer Protocol) and HTTPS (HyperText Transfer Protocol Secure) are two foundational protocols used for transmitting data on the internet, particularly when accessing websites. The main differences between the two relate to security, port usage, and the implementation of SSL/TLS certificates.

## TCP Ports

TCP ports are integral components of the Transport Control Protocol (TCP), one of the core protocols of the Internet Protocol Suite, often referred to as TCP/IP. TCP ports serve as communication endpoints (think of them as door) in the network communications process, allowing different applications or services running on a computer for clients to make requests. After knowing what IP address to connect to to make a request, the port needs to also be specified. Here's an overview of TCP ports and their significance:

### Functionality
- **Endpoints for Communication:** TCP ports enable multiple applications to occur simultaneously on a single computer. Each service can only "bind" to one TCP port represents a specific service or application, facilitating the routing of data to the correct program.
- **Identification:** Each TCP port is identified by a unique number, the port number, ranging from 0 to 65535. Ports are divided into different ranges based on their intended use:

### Port Ranges
- **Well-Known Ports (0-1023):** These ports are reserved for system or well-known services (e.g., HTTP on port 80, HTTPS on port 443). They are regulated and assigned by the Internet Assigned Numbers Authority (IANA).
- **Registered Ports (1024-49151):** Typically used by user applications or processes not provided by the operating system. While less regulated than well-known ports, many are still officially assigned to specific services.
- **Dynamic or Private Ports (49152-65535):** These ports are not officially assigned and can be used by any application for temporary communications. They are often chosen randomly by the operating system when establishing a connection.

# How TCP Ports Work
- **Connection Establishment:** When a service or application wants to communicate over the network, it opens a TCP socket bound to a port number to listen for incoming client requests, like a GET for a webpage.
- **Data Transmission:** Once a connection is established, data packets are sent and received between the computers (knowing their IP addresses) through the associated TCP port. Each packet of information contains the IP address to where it is going and destination port number allowing the receiving system to direct the data to the correct application running on that system.

- **HTTP:** By default, HTTP communicates over port 80. This is the conventional port for web traffic that is not encrypted. When you access a website with HTTP, the data transfer happens in plain text, making it susceptible to eavesdropping and man-in-the-middle attacks.
- Think of **HTTP** like sending a postcard in the mail: anyone can read what is written on the postcard!
- **HTTPS:** HTTPS, on the other hand, uses port 443 by default. This port is reserved for secure communications that are encrypted using SSL/TLS protocols. The encryption ensures that the data transferred between your browser and the website is secure and cannot be easily intercepted or tampered with.
- If HTTP is like sending a postcard, **HTTPS** is putting your letter in a sealed envelope and sending it. Only the address on the envelope can be read, everything else is protected in the sealed envelope and it would be clear if someone else opened it before you got it. 

## SSL/TLS Certificates
- **HTTP:** HTTP does not use SSL/TLS certificates because the data is not encrypted. This lack of encryption means that anyone who can intercept the data can read it (like a postcard)
- **HTTPS:** HTTPS uses SSL (Secure Socket Layer) or TLS (Transport Layer Security) certificates to establish an encrypted connection. The website owner must obtain an SSL/TLS certificate from a Certificate Authority (CA) and install it on their server. This certificate verifies the website's identity and enables secure connections by encrypting the data in transit (like a sealed envelope with a lock (the certificate authority provided values) and key (the unlock keys on the client)).

# Understanding Defaults, required components and Web Browser "Helping"
Portquiz.net is a helpful tool for testing outbound ports and understanding how different ports behave. HTTP will only work using "HTTP", but will respond to requests on any port (as long as your internet provider permits that port to be used--some are blocked for security reasons like 3389 (remote desktop) or 21 (FTP)). 

1. Try connecting to port 8080 using this URL 

```
http://portquiz.net:8080
```
The server responds and the port number, :8080 remains in the URL because it is a non-standard port. Your URL having HTTP as the start tells the browser to make the GET request without any SSL certificate, and the port being specified means the default of 80 will not be used. 

2. Change the 8080 to be another port between 8000 and 9000 and see how the request changes. This working is not normally how a web server works, as usually web servers listen only to one TCP port (the default for HTTP is port 80). It is portquiz.net's function to respond on virtually every port so anyone can test their web browser or internet connection, for example to see if particular outgoing requests targetting specific ports are dropped. 

3. Now, change the port number to be 80 and watch what happens to the URL. Your browser will REMOVE the :80 portion because that is the default, but in reality it is there. You do not need to specify the default port, only put the port if your request is using the non-standard port. Note that your browser also often hides the HTTP:// or HTTPS:// portion of URLs too! It is really there, but the browser tries to make the display "nice" by focusing on the domain itself. As well, entering a URL without this will work. That doesn't mean it isn't "required" per the specification

You can use this tool to experiment with HTTP and HTTPS as follows:

1. **Accessing with HTTP on Port 443:**
   - Try accessing `http://portquiz.net:443`. This attempts to establish an HTTP connection over the port typically used for HTTPS.
   - Since port 443 is conventionally used for secure HTTPS connections, you must specifically make the request using HTTP:// or it will return an SSL error because the request has no certificate.

2. **Accessing with HTTPS on Port 443, the default:**
   - Accessing `https://portquiz.net` (without specifying the port) will use the default HTTPS port (443). This should work normally, as the server expects secure connections on this port. However in this case, the server has no certificate and the request is denied.

3. **Generating an Error:**
   - If you try to access `https://portquiz.net:80`, you're again attempting to establish a secure HTTPS connection over the default HTTP port. Since this website has no capabilities for HTTPS/is not configured for encrypted traffic, the server will not respond correctly, leading to an error or timeout.

