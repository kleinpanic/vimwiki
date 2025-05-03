# Hacking Index and Wiki

--

[funny](funny)

## Overview: 

Hacking refers to the practice of modifying, analyzing, exploiting, or improving systems beyond their original design. While maintstream media often frames it as criminal activity, hacking can be ethical, creative, and innovative. 

--

## Types of Hackers: 

| Types         | Description                                    |
|---------------|------------------------------------------------|
| White Hat     | test systems to find vulnerabilities, legally. |
| Black Hat     | exploit systems for profit or damage.          |
| Grey Hat      | In between. May exploit, often report          |
| Script Kiddie | Uses pre-made tools w/ no understanding        |
| Hacktivist    | Poltiical or Ideaologically motivated exploits |
| Red Team      | Simulating Real World Attacks.                 |
| Blue Team     | Protecting and Responding                      |
|---------------|------------------------------------------------|

Creating a comprehensive Neovim wiki entry for **hacking** can be a powerful tool for learning and reference. Below is a foundational breakdown of **hacking** in an ethical, educational, and technical context, structured as a detailed guide you can adapt for a Neovim `.wiki` or `.md` file. This is exhaustive and modular, so you can add more as you grow.

---

## 🧱 Core Disciplines in Hacking

### 1. **Networking**

- **TCP/IP**, **UDP**, **ICMP**, **ARP**, **DHCP**, **DNS**, etc.
- **OSI Model**
- **Common ports/services** (SSH, FTP, HTTP, SMTP)
- **Tools**: `tcpdump`, `Wireshark`, `nmap`, `netcat`, `ip`, `traceroute`

### 2. **Linux & Shell**

- Command-line proficiency (`bash`, `zsh`)
- Scripting (`bash`, `python`, `perl`)
- File permissions, ownership, processes
- Crons, init systems, systemd

### 3. **Cryptography**

- Hashing: `MD5`, `SHA`, `bcrypt`
- Encryption: `AES`, `RSA`, `ECC`, `GPG`
- SSL/TLS, SSH key management
- Common vulnerabilities: weak encryption, improper key storage

### 4. **Web Exploitation**

- OWASP Top 10: XSS, SQLi, CSRF, SSRF, IDOR
- Tools: `Burp Suite`, `OWASP ZAP`, `Postman`, `curl`, browser dev tools
- Recon: subdomain discovery, directory brute-forcing

### 5. **Binary Exploitation & Reverse Engineering**

- Assembly (`x86`, `x64`, ARM)
- Debuggers: `gdb`, `radare2`, `pwndbg`, `IDA Pro`, `ghidra`
- Exploits: buffer overflows, ROP chains, format strings
- ELF file internals, dynamic vs static analysis

### 6. **Privilege Escalation**

- Linux & Windows escalation paths
- Misconfigured `sudo`, SUID, PATH hijacking
- Kernel exploits
- Windows: `SeImpersonate`, `UAC bypass`, token stealing

### 7. **Social Engineering**

- Phishing, pretexting, baiting, tailgating
- OSINT (Open Source Intelligence)
- Payload delivery: `USB`, malicious links, macro documents

### 8. **Malware Development**

- Languages: `C`, `Python`, `Assembly`
- Techniques: keylogging, rootkits, trojans, ransomware
- Obfuscation, polymorphism, packers

---

## 🛠️ Tools & Frameworks

| Category               | Tools                                                   |
|------------------------|---------------------------------------------------------|
| Recon                  | `nmap`, `amass`, `theHarvester`, `subfinder`, `dnsenum` |
| Exploitation           | `metasploit`, `sqlmap`, `exploitdb`, `searchsploit`     |
| Post-Exploitation      | `Empire`, `PowerSploit`, `Pupy`, `Cobalt Strike`        |
| Forensics              | `Autopsy`, `Volatility`, `binwalk`, `foremost`          |
| Payload Creation       | `msfvenom`, `veil`, `obfuscator-llvm`                   |
| Wireless               | `aircrack-ng`, `hcxdumptool`, `reaver`                  |
| Password Cracking      | `John the Ripper`, `hashcat`, `hydra`                   |
| Container              | `Docker escapes`, `k8s misconfigs`, `runc` exploits     |
| C2 (Command & Control) | `Mythic`, `Sliver`, `Metasploit C2`, `Empire`           |

---

## 🧪 Lab Environments

- **Virtual Machines**: `VirtualBox`, `VMware`, `QEMU`
- **Penetration Testing OS**: `Kali Linux`, `Parrot OS`, `BlackArch`
- **Sandboxed Targets**: `Metasploitable`, `DVWA`, `Hack The Box`, `TryHackMe`, `VulnHub`

---

## ⚙️ Programming for Hackers

| Language   | Use                                  |
|------------|--------------------------------------|
| C          | Exploits, rootkits, buffer overflows |
| Python     | Scripts, automation, PoCs            |
| Bash       | Scripting, enumeration               |
| JavaScript | XSS, browser exploitation            |
| Assembly   | Reverse engineering                  |
| PowerShell | Windows exploitation                 |

