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

## Program:
## Server:
```
server.py
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
## Client:
```
client.py
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
## Server:
<img width="1477" height="348" alt="image" src="https://github.com/user-attachments/assets/334e35e7-8e2b-4987-8971-8ae7b9d9a2f8" />

## Client:

<img width="1469" height="308" alt="image" src="https://github.com/user-attachments/assets/3c492b38-c529-4547-a8d9-eebd1d8d1fb9" />

## Tracert:

<img width="1210" height="403" alt="image" src="https://github.com/user-attachments/assets/1a4b9748-3e4d-401e-ba33-b14878d80db8" />
## IP Config:

<img width="1317" height="702" alt="image" src="https://github.com/user-attachments/assets/2fffa775-44c0-415a-8b82-5fd310543492" />

## nslookup:

<img width="1057" height="522" alt="image" src="https://github.com/user-attachments/assets/d65b7c18-305f-41e8-aee3-74600ae4a854" />

## Netstat:

<img width="889" height="667" alt="image" src="https://github.com/user-attachments/assets/0b0efcd4-e1d0-49d0-acf8-d618916c031a" />

## Result
Thus Execution of Network commands Performed 
