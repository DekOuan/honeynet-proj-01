### First timestamp activitiy  
- The first timestamp activity is 29/Mar/2025:10:00:00Z by starting a CRON job for downloading `malicious.sh`

### Attacker IP address
- I find 203.0.113.5 is the actual public ip address of the attacker all others are private ip addresses
- The private ip address which hacker has accessed to our network is 192.168.1.10, 192.168.1.11, 10.0.0.8

### Reconnaissance techniques
- *Directory and Resource Scanning*: The attacker trying to access the `/admin`, `/phpmyadmin`, `login.php`  path which is not a common path in the website.
- *SSH brute force attempts*: Multiple Failed password for invalid user admin entries
- *Testing access permissions* (seeing what returns 403 Forbidden vs 404 Not Found)
- *Login page testing*: POST /login.php HTTP/1.1 with 200 responses indicating successful attempts
- *Testing default credentials*: Attempts to log in as "admin" user

### Vulnerabilities was exploited by weak credentials
- At the start of the timestamp the attacker was already in the system as the `cron job` was already added and the `malicious script` was already downloaded
- The attacker trying to brute force the password of the admin user
```zsh
Failed password for invalid user admin from 203.0.113.5 port 45678 ssh2
Failed password for invalid user admin from 192.168.1.10 port 45678 ssh2
Failed password for invalid user admin from 192.168.1.11 port 45678 ssh2
Failed password for invalid user admin from 10.0.0.8 port 45678 ssh2
```
- The attacker trying to brute force the password of the root user and successfully logged in
```zsh
Accepted password for root from 203.0.113.5 port 54321 ssh2
Accepted password for root from 192.168.1.10 port 54321 ssh2
Accepted password for root from 192.168.1.11 port 54321 ssh2
```
