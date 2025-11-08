## 4.Execution_of_NetworkCommands

## AIM :
Use of Network commands in Real Time environment

## Software : 
Command Prompt And Network Protocol Analyzer

## Procedure:

To do this experiment, follow these steps:

Students have to understand basic networking commands such as:

tcpdump
netstat
ifconfig
nslookup
traceroute
Additionally, capture ping and traceroute PDUs using a network protocol analyzer.

This includes all commands related to network configuration, such as:

Switching to privileged mode and normal mode
Configuring router interfaces
Saving the configuration to flash memory or permanent memory
This includes the following commands:
Configuring the router commands
General commands to configure network
Privileged mode commands of a router
Router processes & statistics
IP commands
Other IP commands (e.g., show ip route)

## PROGRAM

# 1. Client.py
``` 
 import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
# 2.Server.py
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```
## Output

<img width="765" height="209" alt="image" src="https://github.com/user-attachments/assets/74b8eeaa-a7a1-47cf-ad9a-e0145e3b599e" />


## Result
Thus Execution of Network commands Performed 
