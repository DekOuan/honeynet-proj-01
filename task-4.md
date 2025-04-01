## Indicator of Compromise

### IP Addresses
- `192.168.1.11` - Internal IP trying to SSH attacks, create malicious users and CRON jobs
```zsh
"timestamp": "2025-03-29T11:19:00Z", "log_type": "auth", "client_ip": "192.168.1.11", "event": "Accepted password for root from 192.168.1.11 port 54321 ssh2"
"timestamp": "2025-03-29T10:06:00Z", "log_type": "auth", "client_ip": "192.168.1.11", "event": "new user: name=attacker, UID=1001, GID=1001"
"timestamp": "2025-03-29T11:37:00Z", "log_type": "cron", "client_ip": "192.168.1.11", "event": "CRON executed reverse_shell.py"
```
- `203.0.113.5` - public IP executing `reverse_shell.py` and adding unauthorized user
```zsh
"timestamp": "2025-03-29T10:47:00Z", "log_type": "auth", "client_ip": "203.0.113.5", "event": "Accepted password for root from 203.0.113.5 port 54321 ssh2"
"timestamp": "2025-03-29T12:05:00Z", "log_type": "auth", "client_ip": "203.0.113.5", "event": "new user: name=attacker, UID=1001, GID=1001"
"timestamp": "2025-03-29T12:45:00Z", "log_type": "cron", "client_ip": "203.0.113.5", "event": "CRON executed reverse_shell.py"
```

- `10.0.0.8` - Private IP network range conducting web-attacks and adding a CRON jobs
```zsh
"timestamp": "2025-03-29T11:00:00Z", "log_type": "auth", "client_ip": "10.0.0.8", "event": "new user: name=attacker, UID=1001, GID=1001"
"timestamp": "2025-03-29T10:15:00Z", "log_type": "cron", "client_ip": "10.0.0.8", "event": "CRON executed reverse_shell.py"
"timestamp": "2025-03-29T10:10:00Z", "log_type": "access", "client_ip": "10.0.0.8", "event": "POST /login.php HTTP/1.1 - 200"
```

- `192.168.1.10` - Private IP showing a similar attack pattern as others IPS
```zsh
"timestamp": "2025-03-29T13:00:00Z", "log_type": "auth", "client_ip": "192.168.1.10", "event": "Accepted password for root from 192.168.1.10 port 54321 ssh2"
"timestamp": "2025-03-29T10:01:00Z", "log_type": "auth", "client_ip": "192.168.1.10", "event": "new user: name=attacker, UID=1001, GID=1001"
"timestamp": "2025-03-29T11:29:00Z", "log_type": "cron", "client_ip": "192.168.1.10", "event": "CRON executed reverse_shell.py"
```
