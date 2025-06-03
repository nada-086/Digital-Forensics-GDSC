# HawkEye Blue Team Lab

**Challenge Link:** [HawkEye | Blue Team Challenge](https://cyberdefenders.org/blueteam-ctf-challenges/hawkeye/)

---

## 1. How many packets does the capture have?

- **Answer:** `4003`  
  ![Packets Count](./img/HawkEye-1-1.png)

---

## 2. At what time was the first packet captured?

- **Navigation:** `Statistics` → `Capture File Properties`
- **Answer:** `2019-04-10 20:37:07 UTC`  
  ![First Packet Time](./img/HawkEye-2-1.png)

---

## 3. What is the duration of the capture?

- **Navigation:** `Statistics` → `Capture File Properties`  
  ![Capture Duration](./img/HawkEye-3-1.png)

---

## 4. What is the most active computer at the link level?

- **Navigation:** `Statistics` → `Conversations`
- **Answer:** `00:08:02:1c:47:ae`  
  ![Most Active MAC](./img/HawkEye-4-1.png)

---

## 5. Manufacturer of the NIC of the most active system?

- **Tool:** [MAC Lookup](https://maclookup.app/)
- **Answer:** `Hewlett-Packard`  
  ![NIC Vendor](./img/HawkEye-5-1.png)

---

## 6. Where is the NIC manufacturer headquartered?

- **Answer:** `Palo Alto`  
  ![Headquarters](./img/HawkEye-6-1.png)

---

## 7. How many computers are involved in the capture?

- **Active IPs:** `10.4.10.2`, `10.4.10.4`, `10.4.10.132`
- **Excluded Broadcast IP:** `10.4.10.255`
- **Answer:** `3`  
  ![Involved IPs](./img/HawkEye-7-1.png)

---

## 8. Name of the most active computer at the network level?

- **Filter:** `ip.addr == 10.4.10.132 and frame contains "PC"`
- **Answer:** `Beijing-5cd1-PC`  
  ![Hostname](./img/HawkEye-8-1.png)

---

## 9. What is the IP of the DNS server?

- **Filter:** DNS protocol only
- **Answer:** `10.4.10.4`  
  ![DNS Server](./img/HawkEye-9-1.png)

---

## 10. What domain is queried in packet 204?

- **Answer:** `proforma-invoices.com`  
  ![Domain](./img/HawkEye-10-1.png)

---

## 11. What is the resolved IP of the domain?

- **Answer:** `217.182.138.150`  
  ![Resolved IP](./img/HawkEye-11-1.png)  
  ![DNS Answer](./img/HawkEye-11-2.png)

---

## 12. What country does the IP belong to?

- **Answer:** `France`  
  ![IP Location](./img/HawkEye-12-1.png)

---

## 13. What OS does the victim's machine run?

- **Analysis:** `.exe` download from `10.4.10.132`
- **Answer:** `Windows NT 6.1`  
  ![OS Header](./img/HawkEye-13-1.png)  
  ![OS Version](./img/HawkEye-13-2.png)

---

## 14. Name of the malicious file downloaded?

- **Answer:** `tkraw_Protected99.exe`  
  ![Malicious File](./img/HawkEye-14-1.png)

---

## 15. What is the MD5 hash of the downloaded file?

- **Steps:** `File` → `Export Objects` → `HTTP`
- **Answer:** `71826ba081e303866ce2a2534491a2f7`  
  ![MD5 Hash](./img/HawkEye-15-1.png)

---

## 16. What software runs the malware web server?

- **Answer:** `LiteSpeed`  
  ![Web Server](./img/HawkEye-16-1.png)  
  ![LiteSpeed Header](./img/HawkEye-16-2.png)

---

## 17. What is the public IP of the victim's computer?

- **Public Response IP:** `173.66.146.112` (responding to `10.4.10.132`)
- **Answer:** `173.66.146.112`  
  ![Public IP](./img/HawkEye-17-1.png)

---

## 18. Where is the email server located?

- **SMTP Destination IP:** `23.229.162.69`
- **Answer:** *(From lookup)*  
  ![Email Server IP](./img/HawkEye-18-1.png)

---

## 19. What software runs the email server?

- **Answer:** `EXIM 4.16`  
  ![Email Server Software](./img/HawkEye-19-1.png)

---

## 20. To which email is the stolen info sent?

- **Email:** `sales.del@macwinlogistics.in`  
  ![Target Email](./img/HawkEye-20-1.png)

---

## 21. What is the password used by the malware?

- **Encoded:** Base64 decoded from SMTP auth
- **Answer:** `Sales@23`  
  ![SMTP Auth](./img/HawkEye-21-1.png)

---

## 22. Which malware variant exfiltrated the data?

- **Process:**  
  - Filter SMTP
  - Follow TCP stream
  - Decode base64

  ![Malware 1](./img/HawkEye-22-1.png)  
  ![Malware 2](./img/HawkEye-22-2.png)  
  ![Malware 3](./img/HawkEye-22-3.png)

- **Answer:** *(Based on decoded result, typically HawkEye variant)*

---

## 23. What are the Bank of America credentials?

- **Format:** `username:password`
- **Answer:** *(From decrypted payload)*  
  ![Credentials](./img/HawkEye-23-1.png)

---

## 24. How often is data exfiltrated?

- **Method:** Calculate the time difference between two exfiltration events and divide by 60.
- **Answer:** `10 minutes`  
  ![Exfil Timing](./img/HawkEye-24-1.png)

---