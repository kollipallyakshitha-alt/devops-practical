# Task 2 — What Really Happens When You Stop an Instance

## What I did

### 1. Noted current public IP
Before stopping — 35.179.124.249

### 2. Stopped the instance
Stopped from AWS Console and waited 2 minutes.

### 3. Tried SSH with old IP
ssh -i Akshitha-devops-day2.pem ubuntu@35.179.124.249
Result — connection hung and timed out. No response at all.

### 4. Started the instance again
New public IP after restart — 18.134.206.143
Old IP failed completely.
New IP worked successfully.

### 5. Allocated an Elastic IP
Allocated Elastic IP — 13.135.149.230
Associated it with the instance.
SSH'd in using Elastic IP successfully.

### 6. Stopped and started again
Elastic IP stayed the same — 13.135.149.230
Connected successfully without changing the SSH command.

## Why do public IPs change on stop/start?
When you stop an instance AWS takes back the public IP and returns it to their pool for other customers to use. When you start again AWS gives you a random new IP from whatever is available. Like a taxi — when it parks the number plate goes back to the company and they give it to another taxi.

## What is an Elastic IP?
An Elastic IP is a permanent fixed IP address that belongs to your AWS account. It stays attached to your instance no matter how many times you stop and start. In real projects this is important because if your website points to an IP and that IP keeps changing — nobody can find your website!


