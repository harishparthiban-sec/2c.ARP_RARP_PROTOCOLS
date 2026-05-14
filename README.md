# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### Server.py
```
import socket
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA","10.129.67.111":"C0:A8:10:8A","192.168.1.10":"AA:1B:C3:D4",
"10.0.0.25":"F2:9D:7A:11"};
while True: 
    ip=c.recv(1024).decode() 
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Client.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("\nEnter IP Address of your device : ")
    s.send(ip.encode())
    print("\nMAC Address Of your device :",s.recv(1024).decode())
```
## OUPUT - ARP
<img width="526" height="280" alt="Screenshot 2026-05-14 190135" src="https://github.com/user-attachments/assets/ab8c80ee-2d88-4039-a463-99e32da5aad7" />

## PROGRAM - RARP
### Server.py
```
import socket
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1","C0:A8:10:8A":"10.129.67.111","AA:1B:C3:D4":"192.168.1.10",
"F2:9D:7A:11":"10.0.0.25"};
while True: 
    mac=c.recv(1024).decode() 
    try:
        c.send(address[mac].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Client.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    mac=input("\nEnter MAC Address of your device : ")
    s.send(mac.encode())
    print("\nIP Address Of your device :",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="540" height="306" alt="image" src="https://github.com/user-attachments/assets/9ed751dd-e6d8-4422-9642-656b32c2c32b" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
