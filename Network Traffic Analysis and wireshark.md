## **A. Basics of Packet Capture and Inspection**

### **What is Packet Capture?**

Packet capture is the process of intercepting and recording network packets as they travel across a network interface.

Each packet typically contains:

- **Source IP**
- **Destination IP**
- **Protocol** (TCP, UDP, ICMP, etc.)
- **Payload** (actual data)

Packet captures are saved as:

- `.pcap`
- `.pcapng` (newer, supports more metadata)

These files can be analyzed later without live traffic.

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/ef744d12-1a0f-4518-acbf-330fd040b63f" />

<img width="310" height="163" alt="image" src="https://github.com/user-attachments/assets/65ae3faf-0f5c-4bf4-9ae6-f4f76712c0d0" />

### **Why Packet Inspection Matters**

Packet inspection allows you to:

- Troubleshoot network issues
- Detect malicious traffic
- Understand protocol behavior
- Investigate security incidents

**Confidence level:** High

**Unknowns:** None (core networking concept)

---

## **B. Analyzing Traffic Using Wireshark**

### **What Wireshark Does**

Wireshark is a packet analyzer that:

- Captures live traffic
- Opens `.pcap` / `.pcapng` files
- Decodes hundreds of protocols
- Displays packets in a human-readable format

### **Wireshark Interface Overview**

Main sections:

1. **Packet List Pane** – Summary of packets
2. **Packet Details Pane** – Protocol breakdown
3. **Packet Bytes Pane** – Raw hex and ASCII

<img width="799" height="430" alt="image" src="https://github.com/user-attachments/assets/a7aafe26-62ac-40ac-82e2-319934f40b1b" />

<img width="775" height="277" alt="image" src="https://github.com/user-attachments/assets/75772b10-4c28-4fed-80b2-a10a02567ffb" />

### **Basic Analysis Steps**

1. Open a capture file
2. Apply **display filters** (e.g., `http`, `dns`, `tcp`)
3. Follow conversations (TCP streams)
4. Inspect headers and payloads

Example display filters:

- `ip.addr == 192.168.1.10`
- `tcp.port == 443`
- `dns`

---

## **C. Identifying Anomalous Behavior in Captured Data**

### **What Counts as Anomalous Traffic?**

Traffic that deviates from normal patterns, such as:

- Unexpected protocols
- Suspicious destinations
- Abnormal packet frequency
- Cleartext credentials
- Repeated failed requests

### **Common Indicators of Suspicious Activity**

| Indicator | Explanation |
| --- | --- |
| Excessive DNS requests | Possible tunneling or malware |
| Many SYN packets | Port scanning or DoS attempt |
| Cleartext passwords | Insecure protocols (FTP, HTTP) |
| Unknown IP destinations | Possible C2 servers |
| Repeated ARP replies | ARP spoofing |

<img width="860" height="475" alt="image" src="https://github.com/user-attachments/assets/c98d5d46-109f-47a7-8ea5-d46f162d840b" />

<img width="326" height="155" alt="image" src="https://github.com/user-attachments/assets/b26bc331-7379-4aea-8a7d-e68e079c7c37" />

<img width="888" height="618" alt="image1" src="https://github.com/user-attachments/assets/dda40daf-660c-41d5-bd75-56147f99592b" />

### **How to Detect Anomalies in Wireshark**

- **Statistics → Conversations**
- **Statistics → Protocol Hierarchy**
- **Follow TCP Stream**
- Compare traffic against expected behavior

---
