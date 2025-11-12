# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Program

Server
```
import socket
import os

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")

c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    hostname = c.recv(1024).decode('utf-8')
    if not hostname or hostname.lower() == 'exit':
        print("Client disconnected.")
        break

    try:
        # Use system ping command
        response = os.popen(f"ping -n 4 {hostname}").read()  # Use -c 4 for Linux/Mac
        c.send(response.encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```

Client
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
## Output

Server

<img width="547" height="309" alt="Screenshot 2025-11-12 141821" src="https://github.com/user-attachments/assets/f185606b-66a0-498a-8a19-4b80888d2888" />

Client

<img width="540" height="512" alt="Screenshot 2025-11-12 141903" src="https://github.com/user-attachments/assets/d2a136e4-adef-49b9-a7c6-07f2b28f70fb" />

## Result
Thus Execution of Network commands Performed 
