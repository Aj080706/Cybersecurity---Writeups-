# TryHackMe: Friday Overtime 

Disclaimer

Please note: The artefacts used in this scenario were retrieved from a real-world cyber-attack. Hence, it is advised that interaction with the artefacts be done only inside the attached VM, as it is an isolated environment.
<img width="566" height="396" alt="image" src="https://github.com/user-attachments/assets/76eb1edc-cf53-4bd2-99f4-ed757d11d602" />


Hello Busy Weekend. . .

It's a Friday evening at PandaProbe Intelligence when a notification appears on your CTI platform. While most are already looking forward to the weekend, you realise you must pull overtime because SwiftSpend Finance has opened a new ticket, raising concerns about potential malware threats. The finance company, known for its meticulous security measures, stumbled upon something suspicious and wanted immediate expert analysis.

As the only remaining CTI Analyst on shift at PandaProbe Intelligence, you quickly took charge of the situation, realising the gravity of a potential breach at a financial institution. The ticket contained multiple file attachments, presumed to be malware samples.

With a deep breath, a focused mind, and the longing desire to go home, you began the process of:

1) Downloading the malware samples provided in the ticket, ensuring they were contained in a secure environment.
2) Running the samples through preliminary automated malware analysis tools to get a quick overview.
3) Deep diving into a manual analysis, understanding the malware's behaviour, and identifying its communication patterns.
4) Correlating findings with global threat intelligence databases to identify known signatures or behaviours.
5) Compiling a comprehensive report with mitigation and recovery steps, ensuring SwiftSpend Finance could swiftly address potential threats.

Connecting to the machine

Start the virtual machine in split-screen view by clicking the green Start Machine button on the upper right section of this task. If the VM is not visible, use the blue Show Split View button at the top-right of the page. Additionally, you can open the DocIntel platform using the credentials below.

<img width="450" height="168" alt="image" src="https://github.com/user-attachments/assets/24c36a40-0fa1-4f69-bcdf-01b0829c354b" />

Note: While the web browser (i.e., Chromium) will immediately start after boot up, it may show a tab that has a "502 Bad Gateway" error message displayed. This is because the DocIntel platform takes about 5 more minutes to finish starting up after the VM has completely booted up. After 5 minutes, you can refresh the page in order to view the login page. We appreciate your patience. The ticket details can be found by logging in to the DocIntel platform. OSINT, a web browser, and a text editor outside the VM will also help.


**Q1) Who shared the malware samples?**

I logged on into the Panda Probe platform , where there was a malware sample in the mail. The email also contained the sender's name. 

<img width="308" height="287" alt="image" src="https://github.com/user-attachments/assets/3830c81c-c834-4cda-9b00-da9fa5bd1ba9" />

Answer: Oliver Bennett

**Q2) What is the SHA1 hash of the file "pRsm.dll" inside samples.zip?**

 I downloaded the 'samples.zip' file and then switched to terminal. 
 In terminal I changed the directory to Downloads , where the file was located after extracting the files, I identified the 'pRsm.dll',for sha1 hash i ran the     sha1sum command to get the hash . 

 <img width="661" height="107" alt="image" src="https://github.com/user-attachments/assets/e14caa16-8fd5-4def-908f-e0b202ce528e" />

 Answer: 9d1ecbbe8637fed0d89fca1af35ea821277ad2e8 

 **Q3) Which malware framework utilizes these DLLs as add-on modules?**

 For this question, I uploaded the hash value from previous question in Virustotal, There i found a report related to it. In the report's Key Points section , I found the answer. 


VirusTotal: 
<img width="1117" height="273" alt="image" src="https://github.com/user-attachments/assets/f94d23e5-51a1-4aff-bd8a-4fbd59c2fe87" />

Report: 

<img width="917" height="406" alt="image" src="https://github.com/user-attachments/assets/867fcf76-54b8-4579-bd30-841ef59c5b38" />

Answer:MgBot

**Q4)Which MITRE ATT&CK Technique is linked to using pRsm.dll in this malware framework?**

In the report itself, there was section called 'MITRE ATT&CK techniques'. There i searched 'pRsm.dll' and found the answer. 

<img width="826" height="111" alt="image" src="https://github.com/user-attachments/assets/7c9962ce-f78c-4b9c-9614-74f632065ca0" />

Answer: T1123

**Q5)What is the CyberChef defanged URL of the malicious download location first seen on 2020-11-02?**

In the technical analysis of the report, I found  URL that was of the same date as mentoined in the question. 
I used cyberchef to Defang the URL. 


<img width="807" height="410" alt="image" src="https://github.com/user-attachments/assets/5591821c-997e-455d-b820-7ecf27469687" />

Cyberchef: 

<img width="775" height="130" alt="image" src="https://github.com/user-attachments/assets/63488caf-8811-4a54-82a3-1653d6d88a53" />

Answer: hxxp[://]update[.]browser[.]qq[.]com/qmbs/QQ/QQUrlMgr_QQ88_4296[.]exe

**Q6) What is the CyberChef defanged IP address of the C&C server first detected on 2020-09-14 using these modules?**

I located the C2 server information by referencing the timeline for '2020-09-14'. I then defanged the IP address using CyberChef .


<img width="980" height="76" alt="image" src="https://github.com/user-attachments/assets/212c7ee7-8a46-40c5-8663-00aa9fab525a" />

CyberChef: 

<img width="651" height="87" alt="image" src="https://github.com/user-attachments/assets/b8aebb4f-7821-498e-adc7-a4e8a73d5598" />

Answer: 122[.]10[.]90[.]12

**Q7) What is the md5 hash of the spyagent family spyware hosted on the same IP targeting Android devices in Jun 2025?**

I searched the IP address from the previous question in VirusTotal. I found out about extra information regarding the malware. In the relations tab , There in detections I saw a spyware that was related to android with its MD5 hash. 

<img width="961" height="207" alt="image" src="https://github.com/user-attachments/assets/a96726a6-10c7-44c7-a5e3-b52bda17eb47" />

Answer: 951F41930489A8BFE963FCED5D8DFD79











 



