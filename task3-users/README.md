# Task 3 — Adding a New User with Their Own SSH Key

## What I did

### 1. Created a new user on the server
sudo adduser claudia

### 2. Generated a new SSH key pair on my laptop
ssh-keygen -t ed25519 -f ~/claudia_key
This created two files:
- claudia_key (private key — stays on laptop)
- claudia_key.pub (public key — goes on server)

### 3. Set up SSH access for claudia on the server
sudo mkdir /home/claudia/.ssh
sudo chmod 700 /home/claudia/.ssh
sudo bash -c 'echo "public key" > /home/claudia/.ssh/authorized_keys'
sudo chmod 600 /home/claudia/.ssh/authorized_keys
sudo chown -R claudia:claudia /home/claudia/.ssh

### 4. SSH'd in as claudia from laptop
ssh -i ~/claudia_key claudia@13.135.149.230
Successfully logged in as claudia with her own key!

### 5. Confirmed claudia cannot run sudo
sudo apt update
Result — claudia is not in the sudoers file. Denied!

### 6. Gave claudia sudo access
As ubuntu: sudo usermod -aG sudo claudia
Re-logged in as claudia and sudo apt update worked!

## Explanation of each piece

### The private key (claudia_key on laptop)
This is claudia's secret identity. It stays on her laptop and never gets shared. When she tries to connect SSH uses this key to prove her identity to the server without ever sending the key itself.

### The public key (claudia_key.pub)
This is the shareable half of the key pair. Think of it like a padlock. You can give it to anyone — it is useless without the matching private key to open it.

### authorized_keys on the server
This file lives at /home/claudia/.ssh/authorized_keys and acts like a VIP guest list. It tells SSH — if anyone connecting to claudia's account can prove they have the private key matching any public key in this file — let them in!

### Why permissions matter
SSH has strict security rules. If the .ssh folder or authorized_keys file has loose permissions — anyone on the server could add their own key and get in. So:
- .ssh folder must be chmod 700 — only claudia can read/write/execute
- authorized_keys must be chmod 600 — only claudia can read/write
If permissions are too open SSH will silently refuse the login to protect the server.

