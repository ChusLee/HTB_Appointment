# 🔍 HTB_Appointment
This repository contains a practical penetration testing exercise using Nmap, Gobuster and SQL injection completed during a TryHackMe machine.

## 📌 Objective
The objective is to analyze the machine that HTB provides us to see possible vulnerabilities, exploit them and obtain the flag. 

## 🧰 Tools Used
- Linux Terminal (Kali)
- nmap
- gobuster
- SQL injection

## 📂 Included Files
- `scan_results.txt`: scan output
- `useful_commands.txt`: commented Nmap, Gobuster & SQL injection commands
- `images/`: screenshots from the process

## 📡 Main Command Used
```bash
nmap -sC -sV IP_Target
gobuster --help
gobuster dir --url http://IP_Target/ --wordlist /directory of "directory-list-2.3-small.txt"
SQL and PHP terminology (Usrname = admin'#  / Password = abc123)
