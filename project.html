import socket
import struct

def send_dns_query(domain_name, dns_server="8.8.8.8", port=53):
    """
    Sends a DNS query to the DNS server and returns the response.
    """
    try:
        # Create a UDP socket
        sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        sock.settimeout(5)  # Timeout in seconds

        # Construct DNS query
        transaction_id = 0x1234  # Transaction ID
        flags = 0x0100  # Standard query
        questions = 1
        answer_rrs, authority_rrs, additional_rrs = 0, 0, 0
        header = struct.pack("!HHHHHH", transaction_id, flags, questions, answer_rrs, authority_rrs, additional_rrs)

        # Encode the domain name
        query_name = b""
        for part in domain_name.split("."):
            query_name += struct.pack("!B", len(part)) + part.encode("utf-8")
        query_name += b"\x00"  # End of domain name

        # Query type and class
        query_type = 1  # A record
        query_class = 1  # IN (Internet)
        question = query_name + struct.pack("!HH", query_type, query_class)

        # Full DNS query
        dns_query = header + question

        # Send the query
        sock.sendto(dns_query, (dns_server, port))

        # Receive the response
        response, _ = sock.recvfrom(512)
        return response, transaction_id
    except Exception as e:
        print(f"Error in DNS query: {e}")
        return None, None
    finally:
        sock.close()

def parse_dns_response(response, transaction_id):
    """
    Parses the DNS response and extracts the IP address.
    """
    try:
        header = struct.unpack("!HHHHHH", response[:12])
        if header[0] != transaction_id:
            raise ValueError("Transaction ID mismatch")

        # Skip the question section
        question_end_index = response.find(b"\x00", 12) + 5
        answer_start_index = question_end_index

        # Extract the answer section
        for _ in range(header[3]):  # Number of answer RRs
            # Skip name (pointer) and metadata
            answer_start_index += 12  # Name (2 bytes) + Type/Class/TTL/DataLength (10 bytes)
            ip_address = socket.inet_ntoa(response[answer_start_index:answer_start_index + 4])
            return ip_address
    except Exception as e:
        print(f"Error parsing DNS response: {e}")
        return None

def connect_to_web_server(ip_address, port=80):
    """
    Connects to the web server using the resolved IP address and retrieves content.
    """
    try:
        # Create a TCP socket
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.connect((ip_address, port))
        print(f"Connected to {ip_address} on port {port}")

        # Send an HTTP GET request
        request = f"GET / HTTP/1.1\r\nHost: {ip_address}\r\nConnection: close\r\n\r\n"
        sock.send(request.encode())

        # Receive the response
        response = b""
        while True:
            chunk = sock.recv(4096)
            if not chunk:
                break
            response += chunk

        print("Response from the web server:")
        print(response.decode("utf-8", errors="ignore"))
    except Exception as e:
        print(f"Error connecting to web server: {e}")
    finally:
        sock.close()

def main():
    domain_name = input("Enter the domain name: ").strip()
    if not domain_name:
        print("Invalid domain name.")
        return

    # Step 1: Resolve the domain name
    response, transaction_id = send_dns_query(domain_name)
    if response is None:
        print("Failed to query the DNS server.")
        return

    ip_address = parse_dns_response(response, transaction_id)
    if ip_address:
        print(f"Domain '{domain_name}' resolved to IP: {ip_address}")

        # Step 2: Connect to the web server
        connect_to_web_server(ip_address)
    else:
        print(f"Could not resolve domain '{domain_name}'.")

if __name__ == "__main__":
    main()
