# 2c.SIMULATING ARP /RARP PROTOCOLS

## NAME:A K PREETHI
## REG NO:212223230156
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

## PROGRAM - ARP
## CLIENT
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

## SERVER
import socket

s=socket.socket()

s.connect(('localhost',8000))

while True:

 ip=input("Enter logical Address : ")
 
 s.send(ip.encode())
 
 print("MAC Address",s.recv(1024).decode())
 

## OUPUT - ARP
![Screenshot (2)](https://github.com/PREETHI3312/2c.ARP_RARP_PROTOCOLS/assets/151625222/4e5b5d4e-3de1-4f7f-bc25-bb34f3a4ead3)


## PROGRAM - RARP
## CLIENT
import socket

s=socket.socket()

s.bind(('localhost',8000))

s.listen(5)

c,addr=s.accept()

address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};

while True:

        ip=c.recv(1024).decode()
        
        try:
        
             c.send(address[ip].encode())
             
        except KeyError:
        
            c.send("Not Found".encode())
## SERVER
import socket

s=socket.socket()

s.connect(('localhost',8000))

while True:

        ip=input("Enter MAC Address : ")
        
        s.send(ip.encode())
        
        print("Logical Address",s.recv(1024).decode())


## OUPUT -RARP
![Screenshot (6)](https://github.com/PREETHI3312/2c.ARP_RARP_PROTOCOLS/assets/151625222/4902f667-5f7d-44da-a309-31b8317fbe68)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
