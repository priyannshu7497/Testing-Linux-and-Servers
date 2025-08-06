# Testing-Linux-and-Servers
This project contains a set of shell scripts and configurations as part of a DevOps assignment. It covers:  Linux system monitoring (using htop, df, du)  Secure user account creation (Sarah, Mike) with access controls  Password expiry policies  Automated weekly backups for Apache and Nginx web servers using cron jobs
# DevOps User & Web Server Automation 

## ✅ Task 1: System Monitoring Setup
- Installed `htop`, `df`, and `du` used to monitor system resources.
- Commands used:
  ```bash
  sudo apt install htop
  htop
  df -h
  du -sh /home/*
✅ Task 2: User Management & Access Control
Users created: Sarah and Mike

Secure directories created:

bash
Copy
Edit
sudo mkdir -p /home/Sarah/workspace /home/mike/workspace
sudo chown Sarah:Sarah /home/Sarah/workspace
sudo chmod 700 /home/Sarah/workspace
Password expiry set to 30 days:

bash
Copy
Edit
sudo chage -M 30 Sarah
sudo chage -M 30 mike
✅ Task 3: Backup Automation with Cron Jobs
Created two backup scripts:

/usr/local/bin/backup_apache.sh

/usr/local/bin/backup_nginx.sh

Crontab entry (run every Tuesday at midnight):

cron
Copy
Edit
0 0 * * 2 /usr/local/bin/backup_apache.sh
0 0 * * 2 /usr/local/bin/backup_nginx.sh
📁 Files Included
backup_apache.sh – Script to back up Apache files

backup_nginx.sh – Script to back up Nginx files

README.md – This file

bash
Copy
Edit

---

### 🖥 `backup_apache.sh`
```bash
#!/bin/bash
# Apache Backup Script

BACKUP_DIR="/backups"
DATE=$(date +%F)
ARCHIVE_NAME="apache_backup_$DATE.tar.gz"
VERIFY_LOG="apache_verify_$DATE.log"

tar -czf "$BACKUP_DIR/$ARCHIVE_NAME" /etc/httpd /var/www/html
tar -tzf "$BACKUP_DIR/$ARCHIVE_NAME" > "$BACKUP_DIR/$VERIFY_LOG"
🌐 backup_nginx.sh
bash
Copy
Edit
#!/bin/bash
# Nginx Backup Script

BACKUP_DIR="/backups"
DATE=$(date +%F)
ARCHIVE_NAME="nginx_backup_$DATE.tar.gz"
VERIFY_LOG="nginx_verify_$DATE.log"

tar -czf "$BACKUP_DIR/$ARCHIVE_NAME" /etc/nginx /usr/share/nginx/html
tar -tzf "$BACKUP_DIR/$ARCHIVE_NAME" > "$BACKUP_DIR/$VERIFY_LOG"
