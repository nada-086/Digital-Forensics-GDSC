# Memory Analysis

[Challenge Link](https://app.letsdefend.io/challenge/memory-analysis)

---

1. **What was the date and time when Memory from the compromised endpoint was acquired?**  
   - Use the `windows.info` plugin to retrieve metadata about the memory dump.
     
     ![Memory Info](./img/Memory-Analysis-1-1.png)
   
   - **Answer:** `2022-07-26 18:16:32`

2. **What was the suspicious process running on the system? (Format: name.extension)**  
   - Run `windows.pslist` to review processes.  
   - Notably, `lsass.exe` appears **twice**, which is abnormal.
   - The legitimate `lsass.exe` should be launched by `wininit.exe`.  
   - The second instance with **PID: 7592** is spawned by `explorer.exe`, indicating it’s likely malicious.
     
     ![Duplicate lsass](./img/Memory-Analysis-2-1.png)  
     ![Two lsass Instances](./img/Memory-Analysis-2-2.png)  
     ![Parent Process Check](./img/Memory-Analysis-2-3.png)
   
   - **Answer:** `lsass.exe`

3. **Analyze and find the malicious tool running on the system by the attacker (Format: name.extension)**  
   - Dump files related to the suspicious `lsass.exe` process (PID 7592) using:
     ```bash
     python3 vol.py -f /path-to-dump-file windows.dumpfiles --pid 7592 | grep -i exe
     ```
     
     ![Dump EXEs](./img/Memory-Analysis-3-1.png)
   - Submit the executable to VirusTotal to identify it.
     
     ![VirusTotal](./img/Memory-Analysis-3-2.png)  
     ![winPEAS Detected](./img/Memory-Analysis-3-3.png)
   
   - **Answer:** `winPEAS.exe`

4. **Which User Account was compromised? (Format: DomainName/USERNAME)**  
   - Use `windows.envars` to inspect environment variables of the process.
     
     ![Environment Variables](./img/Memory-Analysis-4-1.png)
   
   - **Answer:** `msedgewin10/cyberjunkie`

5. **What is the compromised user password?**  
   - Use the `windows.hashdump` plugin to extract password hashes from memory.
     
     ![Hashdump](./img/Memory-Analysis-5-1.png)
   - Use an online cracking tool like [CrackStation](https://crackstation.net/) to crack the hash.
     
     ![Cracked Password](./img/Memory-Analysis-5-2.png)
   
   - **Answer:** `password123`