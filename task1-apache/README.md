# Task 1 — Apache Web Server Setup

## What I did

### 1. Launched a new EC2 instance
- Used t3.micro (free tier), Ubuntu 24.04 LTS
- Created a fresh key pair — Akshitha-devops-day2.pem
- Saved it locally in Downloads and set permissions with chmod 400

### 2. Configured Security Group
- Port 22 (SSH) — locked to my IP only
- Port 80 (HTTP) — open to the world
- Everything else — closed

### 3. SSH'd into the server
ssh -i Akshitha-devops-day2.pem ubuntu@35.179.124.249

### 4. Installed Apache
sudo apt update
sudo apt install apache2 -y

### 5. Got system info
uname -a
Linux ip-172-31-33-22 6.17.0-1012-aws #12~24.04.1-Ubuntu SMP Mon Apr 6 17:36:28 UTC 2026 x86_64 x86_64 x86_64 GNU/Linux

### 6. Created custom HTML page
sudo sh -c 'echo "<html>..." > /var/www/html/index.html'

## What broke and how I fixed it
- First tried to open and edit the default Apache file in nano but it had too much code. Fixed by using echo command to overwrite the file directly.
- SSH failed with "Unprotected private key file" error. Fixed by running chmod 400 on the .pem file.

## Live URL
http://35.179.124.249

