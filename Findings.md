
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



## Phase 1 – Initial Traffic Assessment

The investigation began by examining the protocol hierarchy and packet summary in Wireshark.

The capture primarily consists of ICMP Echo Request and Echo Reply packets exchanged between two hosts. The communication is continuous request-response pattern.  

<img width="1225" height="199" alt="image" src="https://github.com/user-attachments/assets/6852c6c3-4a71-4b76-ac8a-0edaeab59bd9" />
<img width="973" height="171" alt="image" src="https://github.com/user-attachments/assets/aef37e2b-6f49-4528-b22f-a30fe8850f54" />



**Evidence**

- Repeated ICMP Echo Request and Echo Reply packets.
- Consistent communication between the same hosts.
- ICMP used as the primary transport protocol.

---

## Phase 2 – Payload Inspection

Each ICMP packet was inspected to determine whether it contained standard diagnostic data or malicious content and to achieve that try to sort icmp packets according to length you will find all the packets are the same size except 23 packets which contain the encapsulated data which are very large in size noted that icmp packets are rubbish data that are used for T.shooting and testing conncetivity.

<img width="1906" height="523" alt="image" src="https://github.com/user-attachments/assets/73dcdf0a-b9f6-4970-8833-cddc5261fc02" />  
<img width="970" height="562" alt="image" src="https://github.com/user-attachments/assets/6c48be24-83c2-478c-a431-9d54829069a6" />  


Inspection of the packet payload revealed plaintext information including:

- Linux login banner
- Username prompt
- Command output


**Evidence**

- `metasploitable login`
- `Password:`
- `uid=1000(msfadmin)`
- `DISPLAY=:0`
- `TERM=xterm`

---



### Indicator 1 – Application Data in ICMP

The ICMP payload contains human-readable shell data instead of standard echo payloads.

### Indicator 2 – Command Execution

Shell commands and their corresponding output are encapsulated within ICMP packets.

### Indicator 4 – Covert Communication

ICMP is being used to transport data beyond its intended diagnostic purpose, creating a covert communication channel.

---

# Findings

The analysis identified the following observations:

- ICMP Echo Request and Echo Reply packets are used throughout the communication.
- ICMP payloads contain interactive shell data.


---

# Conclusion

Based on the packet-level analysis, the captured traffic demonstrates an ICMP tunneling scenario.

