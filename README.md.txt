# Internship Task 1 - Scan Your Local Network For Open Ports


## Objective
To scan the local network for open ports on devices to understand network exposure.

---

# Steps I'am Performed


### 1. Identify My Device ip and subnet 
- checked my ip address with ` ip a ` command.
- i got my ip `192.168.54.30/24`
- This means my network range is `192.168.54.0/24`.

### 2. perform a network scan for identify the live devices in my network
- for this am done this command `nmap -sn 192.168.54.0/24` its gave me active device in my network
- saved this output in `live_devices.txt`

### 3. perform a full scan in my local network 
- to do this using this command `nmap -sS -sV -O -T4 -p- 192.168.54.0/24`
- those flag such as -sS,-sV,-O,-T4,-p- used for respectively for sycn scan, system version , os detection, speed scan with T4 and full port scan 65535 
- saved those output in `full_scan.txt`

### 4. move to pick specific ip from full scan and focusing on it 
- do detailed scan in `192.168.54.163` using `nmap -sS -Pn -p- -O -v 192.168.54.163`
- in this -v flag used for verbose out (more details)
- saved its output in `scan_on192.168.54.163.txt`

### 5. analyze the scan_on192.168.54.163.txt
- find out the open ports on 22 and 80 
- the port 22 used for SSH (Secure Shell) – remote login to another computer 
- the port 80 used for HTTP – loading websites in a browser

### 6. packet capture with wireshark
- open wireshark by type `wireshark` in terminal
- selected my active network interface it was eth0
- start capture 
- then am scan my target ip `192.168.54.163`
- stop capture 
- saved it in `capturepacket.pcapng`

### 7.Optional Filtering:
To analyze specific IP or traffic:
- `ip.addr == <target-ip>`
- `http` (only web traffic)
- `tcp.port == 22` (SSH traffic)


### 8.Research on the port founded in the scan
- port 22 ssh its secure shell protocol used for enable secure remote access to server and other devices
- port 80 html its used for transmiting web content data like web pages imagas videos between the clients

### 9. potential risk on port 22 and 80


## SSH (Secure Shell)
- Weak or default passwords can be brute-forced by attackers.
- Using the default port (22) makes it easier for attackers to target SSH.
- Improper configuration may allow unauthorized remote access.
- Outdated SSH software may have unpatched vulnerabilities.

## HTML (Web Pages)
- Cross-Site Scripting (XSS): Malicious scripts can be injected if user input is not properly sanitized.
- Exposure of sensitive data if HTTPS is not used.
- Vulnerabilities in HTML forms can lead to injection attacks (e.g., SQL Injection).
- Poorly configured CORS policies can expose your site to cross-origin attacks.



## 🔌 Common Network Ports

| Port Number | Service       | Description                 |
|-------------|---------------|-----------------------------|
| 22          | SSH           | Secure remote login          |
| 80          | HTTP          | Unsecured web traffic        |
| 443         | HTTPS         | Secure web traffic (SSL/TLS)|
| 21          | FTP           | File Transfer Protocol       |
| 25          | SMTP          | Email sending                |
| 53          | DNS           | Domain Name System queries   |
| 110         | POP3          | Email receiving              |
| 143         | IMAP          | Email retrieval             |
| 3306        | MySQL         | Database service             |
| 8080        | HTTP Alternate| Alternative web port         |




### Conclusion

- Successfully scanned the network and identified open ports.
- Learned about TCP SYN scan and network reconnaissance.
- Understood the risks of open ports and how to secure them.


## Tools Used

- Nmap
- Terminal on Kali Linux
- wireshark
- google
- AI models like chatgpt for information gathering 



## References

- [Nmap Official Documentation](https://nmap.org/book/man.html)

thank you.....
