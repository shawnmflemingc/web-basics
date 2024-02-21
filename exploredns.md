# Exploring Domain Name System

Understanding how the Domain Name System (DNS) works is crucial in grasping how the internet operates. DNS translates human-readable domain names (like `www.flemingcollege.ca`) into IP addresses that computers use to identify each other on the network. Here’s a simple activity to learn how DNS works, using the command line to perform DNS queries and observe the results:

## Activity Overview
You'll use the `nslookup` command, available on most operating systems, to query domain names and see the IP addresses they resolve to. This activity will help you understand the process of DNS resolution.

### Step 1: Open Your Command Line Interface
Open Windows Command Prompt by typing `cmd` in the search bar, or finding `command prompt` in the start menu.

### Step 2: Basic DNS Lookup
Type the following command and press Enter:
```
nslookup www.flemingcollege.ca
```
Replace `www.flemingcollege.ca` with any domain you're interested in. This command performs a DNS lookup for the domain and returns the corresponding IP address.

### Step 3: Observe the Results
The output will show the server used for the lookup and the IP address for the domain you queried. It might look something like this:
```
Server:  dns.google.com
Address:  8.8.8.8

Non-authoritative answer:
Name:    flemingcollege.ca
Addresses:  192.197.148.31
            2001:500:6b:2::28
```
The "Server" and "Address" at the top refer to the DNS resolver that processed your query, which likely will differ for your local internet setup. The "Name" and "Address" at the bottom show the domain you looked up and its multiple IP address, the first is IPv4, the second is IPv6. 

### Step 4: Reverse DNS Lookup
Now, let's do a reverse lookup, where you query an IP address to find the associated domain name. Enter the following command:
```
nslookup 192.197.148.31
```
Replace `192.197.148.31` with the IP address you obtained from the previous step or any other IP address you're curious about.

### Step 5: Observe the Reverse Lookup Results
The output will show the domain name associated with the IP address you queried. The response might look like this:
```
Name:    www-prod-1.flemingcollege.ca
Address:  192.197.148.31
```
This indicates that the IP address `192.197.148.31` is associated with the domain `flemingcollege.ca`.

### Additional Exploration
- Try different domain names to see how their IP addresses vary.
- Use the `-type=mx` option with `nslookup` to find the mail servers for a domain:
  ```
  nslookup -type=mx flemingcollege.ca
  ```

DNS (Domain Name System) provide more than the website information, it also provides information about its mail servers, and other data. Here are the most common types of DNS records:

### 1. A Record (Address Record)
- **Purpose**: Maps a domain name to an IPv4 address.
- **Example**: `example.com` → `93.184.216.34`

### 2. AAAA Record (IPv6 Address Record)
- **Purpose**: Maps a domain name to an IPv6 address, which is the next generation of IP addresses.
- **Example**: `example.com` → `2606:2800:220:1:248:1893:25c8:1946`

### 3. CNAME Record (Canonical Name Record)
- **Purpose**: Maps an alias name to a true or canonical domain name. This is often used for subdomains.
- **Example**: `www.example.com` might be a CNAME for `example.com`.

### 4. MX Record (Mail Exchange Record)
- **Purpose**: Specifies the mail servers responsible for accepting email on behalf of a domain and their priority.
- **Example**: Points to the mail servers like `mail.example.com` with a priority level (lower numbers have higher priority).

### 5. TXT Record (Text Record)
- **Purpose**: Allows the domain administrator to insert arbitrary text into the DNS record. Often used for email security protocols like SPF (Sender Policy Framework) and DKIM (DomainKeys Identified Mail).
- **Example**: `v=spf1 include:_spf.example.com ~all`

Each of these DNS record types plays a vital role in the operation and management of internet domains, influencing how traffic is routed, how email is delivered, and how domain names are resolved.


### What You Learn
- **DNS Resolution**: How domain names are translated into IP addresses.
- **Reverse DNS Lookup**: Finding the domain name associated with a specific IP address.
- **Nameservers**: The servers that store DNS records for domains.
- **Mail Servers (MX Records)**: The servers that handle email for a domain, and other types of DNS entries.

This activity gives you hands-on experience with DNS, helping you understand how domain names are resolved to IP addresses and vice versa, which is a fundamental aspect of how the internet works.
