# Linux Learning Notes

My notes from learning Linux system administration and DevOps.

## Week 1: Linux Fundamentals

### Day 1: Basic Commands

**Navigation:**
- `pwd` — print working directory
- `ls` — list files
- `ls -la` — list all files with details
- `cd /path` — change directory
- `cd ~` — go home
- `cd ..` — go up one level

**File operations:**
- `touch file.txt` — create empty file
- `mkdir folder` — create directory
- `rm file.txt` — remove file
- `rm -r folder/` — remove directory
- `cp source dest` — copy
- `mv source dest` — move or rename

---

### Day 2: File System

**Important directories:**
- `/home` — user home directories
- `/etc` — configuration files
- `/var` — variable data (logs, databases)
- `/tmp` — temporary files (cleared on reboot)
- `/usr/bin` — user programs

**File viewing:**
- `cat file.txt` — show file content
- `less file.txt` — view file page by page (q to quit)
- `head file.txt` — first 10 lines
- `tail file.txt` — last 10 lines
- `tail -f /var/log/syslog` — follow log in real-time

---

### Day 3: Permissions

**Format:** `rwxr-xr-x`
- r (read) = 4
- w (write) = 2
- x (execute) = 1

**Three groups:**
1. Owner (user)
2. Group
3. Others

**Commands:**
- `chmod 755 file` — rwxr-xr-x
- `chmod 644 file` — rw-r--r--
- `chmod +x script.sh` — add execute permission
- `chown user:group file` — change owner

**Common permissions:**
- `644` — files (owner reads/writes, others read)
- `755` — scripts (owner all, others read/execute)
- `600` — secrets (only owner reads/writes)
- `700` — private folders

---

### Day 4: Users and Groups

**User management:**
- `sudo adduser username` — create user
- `sudo usermod -aG sudo username` — add to sudo group
- `su username` — switch user
- `su - username` — switch with full environment
- `sudo command` — run as root
- `sudo -i` — become root
- `passwd` — change own password
- `sudo passwd username` — change user password

**Information:**
- `whoami` — current user
- `id username` — user ID and groups
- `groups username` — user's groups

**Files:**
- `/etc/passwd` — user list
- `/etc/shadow` — encrypted passwords (root only)
- `/etc/group` — group list

---

### Day 5: Search and Pipes

**find — search files:**
- `find /path -name "file.txt"` — by name
- `find /path -name "*.txt"` — all .txt files
- `find /path -type f` — only files
- `find /path -type d` — only directories
- `find /path -size +10M` — larger than 10MB
- `find / -name "file" 2>/dev/null` — hide permission errors

**grep — search text:**
- `grep "pattern" file.txt` — search in file
- `grep -i "error" file.log` — case-insensitive
- `grep -r "TODO" /project/` — recursive in directory
- `grep -n "root" /etc/passwd` — show line numbers
- `grep -v "exclude" file.txt` — invert match (lines WITHOUT pattern)

**Pipes and text processing:**
- `command1 | command2` — output of cmd1 → input of cmd2
- `cat /etc/passwd | grep root` — filter lines
- `cat file.txt | wc -l` — count lines
- `ps aux | grep nginx` — find process
- `history | grep sudo` — search command history

**Other tools:**
- `wc -l file` — count lines
- `wc -w file` — count words
- `sort file.txt` — sort lines
- `sort -r` — reverse sort
- `uniq` — remove duplicate lines (requires sorted input)
- `sort file | uniq -c` — count occurrences

---

### Day 6: Package Management (APT)

**Update and upgrade:**
- `sudo apt update` — update package list
- `sudo apt upgrade` — upgrade installed packages
- `sudo apt update && sudo apt upgrade -y` — both at once

**Install and remove:**
- `sudo apt install package` — install
- `sudo apt install -y package` — auto-confirm
- `sudo apt remove package` — uninstall
- `sudo apt purge package` — uninstall with configs
- `sudo apt autoremove` — remove unused dependencies

**Search and info:**
- `apt search keyword` — find packages
- `apt show package` — package details
- `apt list --installed` — list installed
- `apt list --upgradable` — what can be updated

**Installed packages:**
- `htop` — interactive process viewer
- `curl` — HTTP client, API requests
- `wget` — download files
- `git` — version control
- `vim` — text editor
- `net-tools` — network utilities (ifconfig, netstat)

---

### Day 7: Git Basics

**Setup:**
- `git config --global user.name "Name"` — set name
- `git config --global user.email "email"` — set email

**Basic workflow:**
- `git init` — initialize repository
- `git add .` — stage all changes
- `git add file.txt` — stage specific file
- `git commit -m "message"` — commit with message
- `git status` — check status
- `git log` — view commit history

**GitHub:**
- `git remote add origin git@github.com:user/repo.git` — link remote
- `git push -u origin main` — push to GitHub
- `git pull` — fetch and merge changes
- `git clone git@github.com:user/repo.git` — clone repository

---

## Useful Combinations

**System info:**
```bash
# Check disk space
df -h

# Check folder size
du -sh /var/log

# Check memory
free -h

# Current IP address
ip a
# or
hostname -I

# System info
uname -a
cat /etc/os-release
```

**Process management:**
```bash
# All processes
ps aux

# Find process
ps aux | grep nginx

# Kill process
kill PID
killall processname

# Top CPU processes
ps aux --sort=-%cpu | head -10

# Top memory processes
ps aux --sort=-%mem | head -10
```

**Logs:**
```bash
# System log
sudo tail -f /var/log/syslog

# Authentication log (SSH logins)
sudo tail -f /var/log/auth.log

# Last 50 lines
sudo tail -50 /var/log/syslog

# Search for errors
sudo grep -i error /var/log/syslog
```

---

## Next Steps

- Week 2: Networking, SSH, Firewall
- Week 3: Bash scripting, Cron automation
- Week 4: Nginx, Web servers
- Month 2: Docker, AWS, VPS setup

---

## Resources

- [DigitalOcean Tutorials](https://digitalocean.com/community/tutorials)
- [Linux Journey](https://linuxjourney.com)
- [Explain Shell](https://explainshell.com) — understand any command

---

*Last updated: 2026-08-05*
