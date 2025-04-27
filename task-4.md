## Indicator of Compromise

### IP Addresses
- The first 3 addresses are private IP which means they are likely compromised device. 
```zsh
- 192.168.1.10
- 192.168.1.11
- 10.0.0.8
- 203.0.113.5
```

### Suspicious files
- `malicious.sh` - Malicious script executed by the attackers
assumed to be a download script from the attacker's C2 server
```zsh
"timestamp": "2025-03-29T10:00:00Z", "log_type": "cron", "client_ip": "192.168.1.10", "event": "CRON job started: wget malicious.sh"
"timestamp": "2025-03-29T10:05:00Z", "log_type": "cron", "client_ip": "10.0.0.8", "event": "CRON job started: wget malicious.sh"
"timestamp": "2025-03-29T11:18:00Z", "log_type": "cron", "client_ip": "203.0.113.5", "event": "CRON job started: wget malicious.sh"
```

- `reverse_shell.py` - Malicious script executed by the attackers located in `/tmp/reverse_shell.py`
```zsh
"timestamp": "2025-03-29T10:02:00Z", "log_type": "cron", "client_ip": "203.0.113.5", "event": "CRON executed reverse_shell.py"
"timestamp": "2025-03-29T10:15:00Z", "log_type": "cron", "client_ip": "10.0.0.8", "event": "CRON executed reverse_shell.py"
"timestamp": "2025-03-29T11:37:00Z", "log_type": "cron", "client_ip": "192.168.1.11", "event": "CRON executed reverse_shell.py"
```


- `etc/passwd` - attacker likely to add attacker to user account
```zsh
Modified: /etc/passwd
```

### URL that was used by the attacker
- `/config.php` - attacker trying to access the configuration file of the web application
```zsh
"timestamp": "2025-03-29T10:18:00Z", "log_type": "access", "client_ip": "192.168.1.11", "event": "GET /config.php HTTP/1.1 - 403"
"timestamp": "2025-03-29T10:19:00Z", "log_type": "access", "client_ip": "192.168.1.10", "event": "GET /config.php HTTP/1.1 - 403"
"timestamp": "2025-03-29T10:19:00Z", "log_type": "access", "client_ip": "203.0.113.5", "event": "GET /config.php HTTP/1.1 - 403"
```

- `/login.php` - attacker trying to access the login page of the web application
```zsh
"timestamp": "2025-03-29T10:10:00Z", "log_type": "access", "client_ip": "10.0.0.8", "event": "POST /login.php HTTP/1.1 - 200"
"timestamp": "2025-03-29T10:35:00Z", "log_type": "access", "client_ip": "203.0.113.5", "event": "POST /login.php HTTP/1.1 - 200"
"timestamp": "2025-03-29T11:30:00Z", "log_type": "access", "client_ip": "192.168.1.10", "event": "POST /login.php HTTP/1.1 - 200"
```

- `/phpmyadmin` - attacker trying to access the phpMyAdmin page of the web application
```zsh
"timestamp": "2025-03-29T10:04:00Z", "log_type": "access", "client_ip": "192.168.1.11", "event": "GET /phpmyadmin/ HTTP/1.1 - 404"
"timestamp": "2025-03-29T10:53:00Z", "log_type": "access", "client_ip": "10.0.0.8", "event": "GET /phpmyadmin/ HTTP/1.1 - 404"
"timestamp": "2025-03-29T11:03:00Z", "log_type": "access", "client_ip": "10.0.0.8", "event": "GET /phpmyadmin/ HTTP/1.1 - 404"
```

- `/admin` - attacker trying to access the admin page of the web application
```zsh
"timestamp": "2025-03-29T10:20:00Z", "log_type": "access", "client_ip": "10.0.0.8", "event": "GET /admin HTTP/1.1 - 403"
"timestamp": "2025-03-29T10:59:00Z", "log_type": "access", "client_ip": "192.168.1.10", "event": "GET /admin HTTP/1.1 - 403"
"timestamp": "2025-03-29T12:06:00Z", "log_type": "access", "client_ip": "192.168.1.11", "event": "GET /admin HTTP/1.1 - 403"
```

### SHA-256 hash of the malicious script
```zsh
Added: /tmp/reverse_shell.py SHA256: d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2
```
