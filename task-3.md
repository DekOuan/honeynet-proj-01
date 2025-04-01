`network_traffic.txt`

```zsh
192.168.1.11 -> 10.0.0.5:443 (C2)
192.168.1.11 -> 10.0.0.6:80 (HTTP Download)

```
### C2
- The attacker is using a C2 server to control the compromised machine
- The C2 server is at `10.0.0.5:443`

### HTTP Download
- The attacker is downloading a file from `10.0.0.6:80`

### Malicious script
```
Mar 29 10:25:01 CRON[1236]: (attacker) CMD (/usr/bin/python3 /tmp/reverse_shell.py)
```
- The attacker is executing a script called `reverse_shell.py` as a cron job

