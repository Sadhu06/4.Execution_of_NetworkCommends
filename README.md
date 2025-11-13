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
import subprocess
import platform

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server listening on port 8000...")
c, addr = s.accept()
print("Connected:", addr)

while True:
    command = c.recv(1024).decode().strip()
    if not command or command.lower() == 'exit':
        print("Client disconnected.")
        break

    try:
        # Run ANY command the client sends
        completed = subprocess.run(
            command, 
            capture_output=True, 
            text=True, 
            shell=True
        )
        output = completed.stdout + (completed.stderr or "")
    except Exception as e:
        output = f"Command failed: {e}"

    c.sendall(output.encode('utf-8'))

c.close()
s.close()
```

Client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

print("Connected. Type any network command (ipconfig, ping, etc.) or 'exit'.")

while True:
    cmd = input("Enter command: ").strip()
    if not cmd:
        continue

    s.send(cmd.encode('utf-8'))
    
    if cmd.lower() == "exit":
        print("Exiting...")
        break

    output = s.recv(65536).decode()
    print("\n----- RESULT -----")
    print(output)
    print("------------------\n")

s.close()
```
## Output

netstat

<img width="1054" height="834" alt="Screenshot 2025-11-13 155705" src="https://github.com/user-attachments/assets/1fac4124-adae-485d-b0e9-a55348c25610" />

ipconfig

<img width="1057" height="804" alt="Screenshot 2025-11-13 155918" src="https://github.com/user-attachments/assets/f404e379-adfd-41aa-8faf-edaa4bcec7ad" />

ping

<img width="1054" height="429" alt="Screenshot 2025-11-13 160007" src="https://github.com/user-attachments/assets/c1817473-9364-4d79-ac20-57bb0e02a228" />

tracert

<img width="1048" height="463" alt="Screenshot 2025-11-13 160049" src="https://github.com/user-attachments/assets/d2298125-ff84-4cd2-bff7-2fb9a1124239" />

nslookup

<img width="732" height="371" alt="Screenshot 2025-11-13 160823" src="https://github.com/user-attachments/assets/36aa7889-0afa-4154-a3a2-67f70bff124a" />

getmac

<img width="840" height="284" alt="Screenshot 2025-11-13 160909" src="https://github.com/user-attachments/assets/a7434173-aa1c-47f1-aaff-40911401ad57" />

hostname

<img width="657" height="203" alt="Screenshot 2025-11-13 160942" src="https://github.com/user-attachments/assets/ec1fadcb-5dd0-4111-938b-a27c4cb6e26e" />

nbtstat

<img width="1006" height="711" alt="Screenshot 2025-11-13 161021" src="https://github.com/user-attachments/assets/91e097c4-33bd-4b41-948e-91710da79c62" />

arp

<img width="1011" height="894" alt="Screenshot 2025-11-13 161108" src="https://github.com/user-attachments/assets/b54d71be-d71a-4fd2-8697-15d97a9f98d5" />

systeminfo

<img width="1014" height="926" alt="Screenshot 2025-11-13 161159" src="https://github.com/user-attachments/assets/4aff77c5-9cb2-4abc-81f8-a48611a5b33f" />



## Result
Thus Execution of Network commands Performed 
