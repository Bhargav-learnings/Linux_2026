# Linux Most-Used Commands
---

## File & Directory Commands

ls            → list files  
ls -l         → detailed listing  
ls -a         → include hidden files  
pwd           → current directory  
cd /path      → change directory  

mkdir dir     → create directory  
mkdir -p a/b  → create parent directories  

rm file       → delete file  
rm -r dir     → delete directory  
rm -rf dir    → force delete (dangerous)

cp file1 file2        → copy file  
cp -r dir1 dir2       → copy directory  

mv file1 file2        → move/rename file  

---

## File Viewing & Editing

cat file             → view file content  
less file            → scrollable view  
more file            → paginated view  

head file            → first 10 lines  
head -n 20 file      → first 20 lines  

tail file            → last 10 lines  
tail -f app.log      → live log monitoring  

touch file           → create empty file  

---

## Permissions & Ownership

ls -l                → view permissions  

chmod 755 file       → change permissions  
chmod u+x file       → add execute permission  

chown user file      → change owner  
chown user:group f   → change owner & group  

chgrp group file     → change group  

umask                → view default permissions  

---

## User & Group Management

whoami               → current user  
id user              → UID and GID  

useradd user         → create user  
userdel user         → delete user  
userdel -r user      → delete user with home  

groupadd group       → create group  
groupdel group       → delete group  

usermod -aG grp usr  → add user to group  

---

## Process Management

ps -ef               → all processes  
ps aux               → process snapshot  

top                  → real-time process view  
htop                 → enhanced top  

kill PID             → terminate process  
kill -9 PID          → force kill  

nice -n 10 cmd       → set priority  
renice -5 PID        → change priority  

---

## CPU & Memory

free -h              → memory usage  
uptime               → load average  

vmstat               → memory & CPU stats  
mpstat               → CPU stats  

---

## Disk & Filesystem

df -h                → disk usage  
df -i                → inode usage  

du -sh dir           → directory size  
du -sh *             → size of all items  

lsblk                → block devices  
mount                → mounted filesystems  
umount /mnt          → unmount filesystem  

mount -a             → mount from fstab  

---

## Networking

ip a                 → IP addresses  
ip r                 → routing table  

ping host            → connectivity test  
curl url             → HTTP request  

ss -tulnp            → listening ports  
netstat -plant       → port & process info  

---

## Logs & Troubleshooting

tail -f app.log      → follow logs  

grep ERROR app.log   → search logs  
grep -i fail auth.log→ case-insensitive search  

awk '{print $1}' f  → extract columns  
sed 's/a/b/g' f     → replace text  

journalctl           → system logs  
journalctl -u svc    → service logs  
journalctl -f        → live logs  

---

## Service Management (systemd)

systemctl status svc → service status  
systemctl start svc  → start service  
systemctl stop svc   → stop service  
systemctl restart svc→ restart service  

systemctl enable svc → start at boot  
systemctl disable svc→ disable at boot  

systemctl daemon-reload → reload unit files  

---

## SSH & Access

ssh user@host        → SSH login  

ssh-keygen           → generate SSH keys  
ssh-copy-id user@ip  → copy public key  

chmod 600 id_rsa     → private key permission  
chmod 700 ~/.ssh     → SSH directory permission  

---

## Package Management

### RHEL / Amazon Linux
yum install pkg  
dnf install pkg  
yum remove pkg  
yum update  

### Ubuntu / Debian
apt update  
apt install pkg  
apt remove pkg  
apt upgrade  

---

## Troubleshooting Power Commands (INTERVIEW GOLD)

lsof | grep deleted  → find deleted files still in use  
df -h && df -i       → disk & inode check  

top + logs           → CPU issue debugging  
journalctl -xe       → service failure debugging  
