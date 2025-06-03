# l337 S4uc3 | Blue Team Lab

[Challenge Link](https://cyberdefenders.org/blueteam-ctf-challenges/l337-s4uc3/)

---

1. **What is the public IP address of the webserver?**  
   - Filter: `http and frame contains "development.wse.local"`  
   - Source IP in response packet:  
   - ![Packet](./img/l337-S4uc3-1-3.png)  
   - **Answer:** `74.204.41.73`

2. **Arrival time of frame 1 in UTC (GrrCON.pcapng)?**  
   - Set time format to UTC under View → Time Display Format.  
   - ![Timestamp](./img/l337-S4uc3-2-1.png)  
   - **Answer:** `22:51:07 UTC`

3. **What PHP version is the server running?**  
   - Found in HTTP response headers.  
   - ![PHP Version](./img/l337-S4uc3-3-1.png)  
   - **Answer:** `5.3.2`

4. **What Apache version is the server using?**  
   - Found in HTTP response headers.  
   - ![Apache Version](./img/l337-S4uc3-4-1.png)  
   - **Answer:** `2.2.14`

5. **Common name of malware in IDS alert?**  
   - ![IDS Alert](./img/l337-S4uc3-5-1.png)  
   - **Answer:** `zeus`

6. **What is the Gateway IP address of the LAN?**  
   - Review ARP broadcast packets.  
   - ![Gateway](./img/l337-S4uc3-6-2.png)  
   - **Answer:** `172.16.0.1`

7. **What IP address was pinged by Zeus bot to verify connectivity?**  
   - ![Pinged IP](./img/l337-S4uc3-7-1.png)  
   - **Answer:** `74.125.225.112`

8. **What is the Zeus C2 server IP address?**  
   - Filter: `http and frame contains ".bin"`  
   - ![C2 IP](./img/l337-S4uc3-8-2.png)  
   - **Answer:** `88.198.6.20`

9. **Filename of the Zeus bot ".bin" config file?**  
   - ![Config File](./img/l337-S4uc3-9-1.png)  
   - **Answer:** `cf.bin`

10. **What was the WordPress login password used at 6:59 PM EST?**  
    - Source IP: `172.16.0.108`  
    - ![Password](./img/l337-S4uc3-10-2.png)  
    - **Answer:** *(Extracted from screenshot)*

11. **Access time of the designs page using password `1qBeJ2Az`?**  
    - Filter: `http and frame contains "1qBeJ2Az"`  
    - ![Access Time](./img/l337-S4uc3-11-2.png)  
    - **Answer:** `23:04:04 UTC`

12. **Source port in shellcode exploit (dest port 31708)?**  
    - Filter: `tcp.dstport == 31708 or udp.dstport == 31708`  
    - ![Shellcode Packet](./img/l337-S4uc3-12-1.png)  
    - **Answer:** *(Extracted from packet info)*

13. **Linux kernel version returned from `sysinfo`?**  
    - ![Kernel Info](./img/l337-S4uc3-13-2.png)  
    - **Answer:** `2.6.32-38-server`

14. **Token value in frame 3897?**  
    - ![Token](./img/l337-S4uc3-14-1.png)  
    - **Answer:** `b7aad621db97d56771d6316a6d0b71e9`

15. **Tool used to download compressed file?**  
    - Filter: `http.request.method == "GET" and (frame contains ".zip" or ".rar" or ".tar")`  
    - ![Tool](./img/l337-S4uc3-15-1.png)  
    - **Answer:** `Wget`

16. **Download filename used to launch Zeus bot?**  
    - ![Filename](./img/l337-S4uc3-16-1.png)  
    - **Answer:** `bt.exe`

17. **Full file path of system shell spawned via meterpreter session?**  
    - Used plugins: `imageinfo`, `linux_pslist`, `linux_pstree`, `linux_psaux`  
    - ![Shell Path](./img/l337-S4uc3-17-4.png)  
    - **Answer:** `/bin/sh`

18. **Parent Process ID (PPID) of the two 'sh' sessions?**  
    - ![PPID](./img/l337-S4uc3-18-1.png)  
    - **Answer:** `1042`

19. **Latency record count for PID 1274?**  
    - Used `linux_volshell` and process offset.  
    - ![Latency Record](./img/l337-S4uc3-19-3.png)  
    - **Answer:** `0`

20. **First mapped file path for PID 1274?**  
    - Plugin: `linux_proc_map`  
    - ![Mapped Path](./img/l337-S4uc3-20-2.png)  
    - **Answer:** `/bin/dash`

21. **MD5 hash of `receive.1105.3` from per-process packet queue?**  
    - Used `linux_pkt_queues` and `md5sum`  
    - ![MD5 Hash](./img/l337-S4uc3-21-1.png)  
    - **Answer:** `184c8748cfcfe8c0e24d7d80cac6e9bd`