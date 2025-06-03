# PCAP Analysis

**Challenge Link:** [Getting Started to LetsDefend](https://app.letsdefend.io/challenge/pcap-analysis#virtual)

---

## 1. What are the IP addresses of the sender and receiver in the network communication?

- By reviewing Wireshark conversations, the device with IP `192.168.235.137` is causing malicious traffic, indicating this is the attacker IP likely targeting our internal network.  
  ![Attacker IP](./img/PCAP-1-1.png)

- Searching traffic between private IPs reveals communication between the attacker IP and another private IP.  
  ![Traffic Search](./img/PCAP-1-2.png)

- **Answer:** `192.168.235.137`, `192.168.235.131`

---

## 2. What is the IP address of the web server to which a file was uploaded?

- **Answer:** `192.168.235.137`  
  ![Server IP](./img/PCAP-2-1.png)

---

## 3. What is the name of the file sent through the network?

- Review the HTTP POST packet response for details.  
  ![File Name Packet](./img/PCAP-3-1.png)

- **Answer:** `file`  
  ![File Name](./img/PCAP-3-2.png)

---

## 4. What is the name of the web server hosting the upload?

- From the same packet in question 3.  
- **Answer:** `Apache`  
  ![Web Server](./img/PCAP-4-1.png)

---

## 5. What directory was the file uploaded to?

- From the same packet in question 3.  
- **Answer:** `uploads`  
  ![Upload Directory](./img/PCAP-5-1.png)

---

## 6. How long did it take the sender to send the encrypted file?

- Filter traffic between attacker and server. Subtract the time of the last TCP packet from the first TCP packet.  
  ![Time Taken](./img/PCAP-6-1.png)

- **Answer:** `0.0073` seconds

---