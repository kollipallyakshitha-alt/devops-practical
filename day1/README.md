#Day 1 - devops practial (19th may)
## What I did 
### 1.Lanched an EC2 instance on AWS
-> used ubuntu 24.04 LTS(22.0 is not available), t3.micro (t2,micro is not available)
->created a freshkey pair -akshitha-devops-key.pem
->saved key locally in ssh and set permissions with chmod 400
### 2. Configured security group
->port 22 - type-shh,locked to my ip only , 
-> port 80 - type-http, open to the world 
everything else -closed 
### 3. SSH into server 
-> ssh -i ~/.ssh/akshitha-devops-key.pem ubuntu@3.95.172.206
### 4. installed Nginx
->  Nginx is a web server that serves webpages to visitors
->sudo apt update 
->sudo apt install nginx -y
->sudo systemct1 status nginx
### 5. Created a html page 
->sudo nan0/var/www/html/index.html
->added hell0 from akshitha, a small line into it 
-> verified at http://3.95/172.206
##what broke and how i fixed it 
-> first EC2 launch failed - selected ubuntu 22.o4 with sql server , where i have to select 22.04 lts ,as their is no 22.04 ther version i went with ubuntu 24.04 Lts ans also i did not have t2.micro , I used t3.micro 
-> In HTML page ,it showed a strange character in the "-" place ,fixed by adding charset UTF-8 in html head.
## stretch 
### Does Nginx come back after reboot?
->Yes, After running sudo reboot and SSHing back in, Nginx was already running. This is because it is enabled as a systemd service which starts automatically on boot.

### Where is Nginx configured to look for files?
In /etc/nginx/sites-available/default the root is set to /var/www/html — that is why editing index.html there served our custom page.
 
