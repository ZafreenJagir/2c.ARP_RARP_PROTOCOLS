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
CLIENT.PY:
```
import socket 
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

SERVER.PY
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address: ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
CLIENT.PY



![Screenshot 2024-04-27 182508](https://github.com/ZafreenJagir/2c.ARP_RARP_PROTOCOLS/assets/144870573/ba376c96-7f78-48b4-90f8-8ec108059367)

SERVER.PY




![Screenshot 2024-04-27 182520](https://github.com/ZafreenJagir/2c.ARP_RARP_PROTOCOLS/assets/144870573/16edff92-d28e-4999-a8f9-f4367060c761)

## PROGRAM - RARP
CLIENT.PY
```
import socket 
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())


```
SERVER.PY
``` 
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
   ip=input("Enter MAC Address: ")
   s.send(ip.encode())
   print("IP Address",s.recv(1024).decode())


```
## OUPUT -RARP
CLIENT.PY




![Screenshot 2024-04-27 182846](https://github.com/ZafreenJagir/2c.ARP_RARP_PROTOCOLS/assets/144870573/b082ae43-93f7-4966-9699-6a0c35f07c3c)

SERVER.PY




![Screenshot 2024-04-27 182906](https://github.com/ZafreenJagir/2c.ARP_RARP_PROTOCOLS/assets/144870573/3ec2d3cc-c0ed-4d5e-a1f5-7c94c0bdf4d1)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
