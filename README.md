# DNS Resolver and Web Server Connector
This project implements a **simple DNS Resolver in Python** that manually constructs and sends DNS queries to a DNS server, resolves a domain name into its corresponding IP address, and then establishes a connection with the target web server using sockets. It demonstrates the working principles of DNS resolution, network communication, and HTTP requests without relying on high-level libraries. 

## Features
* Manually constructs DNS query packets.
* Sends DNS requests using UDP sockets.
* Parses DNS responses to extract IP addresses.
* Resolves domain names to IPv4 addresses.
* Establishes TCP connection with the resolved web server.
* Sends HTTP GET requests.
* Retrieves and displays server responses.
  

## Technologies Used
* Python
* Socket Programming
* UDP Protocol
* TCP Protocol
* DNS Protocol
* HTTP Protocol
* Struct Module

## Working Process

```text
User enters domain name
          │
          ▼
Construct DNS Query Packet
          │
          ▼
Send Query to DNS Server (8.8.8.8)
          │
          ▼
Receive DNS Response
          │
          ▼
Extract IP Address
          │
          ▼
Connect to Web Server
          │
          ▼
Send HTTP GET Request
          │
          ▼
Receive and Display Response
```

## Project Structure

```text
DNS-Resolver/
│
├── dns_resolver.py
├── README.md
└── requirements.txt
```


## How to Run

### Clone the Repository
```bash
git clone https://github.com/your-username/DNS-Resolver.git
cd DNS-Resolver
```
### Run the Program
```bash
python dns_resolver.py
```
### Example
```text
Enter the domain name: google.com

Domain 'google.com' resolved to IP: 142.250.xxx.xxx

Connected to 142.250.xxx.xxx on port 80

Response from the web server:
HTTP/1.1 200 OK
...
```
