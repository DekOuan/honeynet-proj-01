### SSH Access
```zsh
Mar 29 10:21:03 honeypot sshd[1234]: Accepted password for root from 192.168.1.11 port 54321 ssh2
Mar 29 10:22:15 honeypot useradd[1235]: new user: name=attacker, UID=1001, GID=1001
```
- The attacker succesfully logged in as root user
- The attacker created a new user called `attacker`

### Cron Job
```zsh
CRON job added by attacker
CRON job started: wget malicious.sh
```
### Malicious script
- The attacker added a cron job to download a malicious script
```zsh
CRON executed reverse_shell.py
```
The attacker executed a script called `reverse_shell.py`
