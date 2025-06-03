# Disclose The Agent

[Getting Started to LetsDefend](https://app.letsdefend.io/challenge/disclose-the-agent)

---

1. **What is the email address of Ann's secret boyfriend?**  
   - Use the filter `smtp and frame contains ".com"` to show SMTP packets containing email addresses.  
     
     ![SMTP Filter](./img/Disclose-The-Agent-1-1.png)  
   
   - There are only three distinct emails found in the capture.  
     
     ![Emails Found](./img/Disclose-The-Agent-1-2.png)  
   
   - **Answer:** `mistersecretx@aol.com`  
     
     ![Secret Email](./img/Disclose-The-Agent-1-3.png)

2. **What is Ann's email password?**  
   - Inspect the SMTP packets for login information.  
     
     ![Password Packet](./img/Disclose-The-Agent-2-1.png)  
   
   - The password is shown as `NTU4cjAwbHo=` which is Base64 encoded.  
     
     ![Base64 Password](./img/Disclose-The-Agent-2-2.png)  
   
   - Decoding the Base64 string gives: `558r00lz`

3. **What is the name of the file that Ann sent to her secret lover?**  
   - Find the SMTP packet where Ann sends the file to her lover.  
     
     ![File Packet](./img/Disclose-The-Agent-3-1.png)  
   
   - Follow the TCP Stream of this packet to view the transmitted data.  
     
     ![TCP Stream](./img/Disclose-The-Agent-3-2.png)  
   
   - **Answer:** `secretrendezvous.docx`

4. **In what country will Ann meet with her secret lover?**  
   - Export the email object from the packet capture (select `rendezvous.eml`) and save it.  
     
     ![Export Email](./img/Disclose-The-Agent-4-1.png)  
   
   - Open the saved `.eml` file and examine its contents.  
     
     ![Open Email](./img/Disclose-The-Agent-4-2.png)  
   
   - Open the attached file inside the email to find the meeting location.  
     
     ![Attachment](./img/Disclose-The-Agent-4-3.png)  
   
   - **Answer:** Mexico

5. **What is the MD5 value of the attachment Ann sent?**  
   - Use any online MD5 hash calculator to get the hash of the attachment file.  
     
     [Online MD5 Calculator](https://md5file.com/calculator)  
   
   - **Answer:** `9e423e11db88f01bbff81172839e1923`  
     
     ![MD5 Hash](./img/Disclose-The-Agent-5-1.png)