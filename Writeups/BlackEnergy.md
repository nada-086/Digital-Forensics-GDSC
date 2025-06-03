# BlackEnergy Blue Team Lab

[Challenge Link](https://cyberdefenders.org/blueteam-ctf-challenges/blackenergy/)

---

1. **Which volatility profile would be best for this machine?**  
   - Use `imageinfo` to find suggested profiles. Confirm with `kdbgscan`.
   - ![imageinfo](./img/BlackEnergy-1-1.png)  
   - ![kdbgscan](./img/BlackEnergy-1-2.png)  
   - **Answer:** `WinXPSP2x86`

2. **How many processes were running when the image was acquired?**  
   - Use `pslist`. Total: 25; Exited: 6.
   - ![Processes](./img/BlackEnergy-2-1.png)  
   - ![Exited Processes](./img/BlackEnergy-2-2.png)  
   - **Answer:** `19`

3. **What is the process ID of cmd.exe?**  
   - ![cmd.exe PID](./img/BlackEnergy-3-1.png)  
   - **Answer:** `1960`

4. **What is the name of the most suspicious process?**  
   - ![Suspicious Process](./img/BlackEnergy-4-1.png)  
   - **Answer:** `rootkit.exe`

5. **Which process shows the highest likelihood of code injection?**  
   - Use `malfind`.
   - ![Malfind Result](./img/BlackEnergy-5-1.png)  
   - **Answer:** `svchost.exe`

6. **There is an odd file referenced in the recent process. Provide the full path of that file.**  
   - Use `handles`.
   - ![Handles](./img/BlackEnergy-6-1.png)  
   - ![str.sys path](./img/BlackEnergy-6-2.png)  
   - **Answer:** `C:\Windows\System32\drivers\str.sys`

7. **What is the name of the injected DLL file loaded from the recent process?**  
   - Use `ldrmodules` to identify DLLs that are hidden.
   - ![Injected DLL](./img/BlackEnergy-7-1.png)  
   - **Answer:** `msxml3r.dll`

8. **What is the base address of the injected DLL?**  
   - Use `malfind`.
   - ![Base Address](./img/BlackEnergy-8-1.png)  
   - **Answer:** `0x980000`