# Background

## What is Tunneling?

Network tunneling is a technique that encapsulates one protocol or type of traffic inside another protocol. While tunneling has legitimate uses, attackers can abuse it to bypass network restrictions or firewalls, establish communication channels, or hide malicious activity.

## Common Types of Tunneling

- **ICMP Tunneling** – Encapsulates data within ICMP Echo Request and Echo Reply packets.
- **DNS Tunneling** – Transfers data through DNS queries and responses.
- **HTTP/HTTPS Tunneling** – Uses web traffic to transport malicious communication.
- **SSH Tunneling** – Creates encrypted tunnels for secure communication or port forwarding.
- **TCP/UDP Tunneling** – Encapsulates traffic within TCP or UDP connections.

## ICMP Tunneling

ICMP tunneling uses ICMP packets to carry data instead of their normal diagnostic purpose. Since ICMP traffic is commonly allowed through network devices, attackers may use it to establish command-and-control (C2) channels, transfer data, or obtain remote shell access while attempting to avoid detection.
