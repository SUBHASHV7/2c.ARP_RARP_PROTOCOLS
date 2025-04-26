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

Developed By : SUBHASH V

Reg No       : 212224240163

## PROGRAM - ARP
*server.py*
~~~
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
~~~
*client.py*
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
~~~
## OUPUT - ARP

# SERVER
![434648204-0cfda9d1-2754-4973-bcf7-055cc8385921](https://github.com/user-attachments/assets/6b7309ef-ed16-461c-b794-12cd25c087fb)

# CLIENT
![434648424-ef2b17d1-a115-4860-9a76-6144263f1651](https://github.com/user-attachments/assets/c94dbec4-7979-490b-8de0-33703204f9cc)


## PROGRAM - RARP
*server.py*
~~~
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    mac=c.recv(1024).decode()
    try:
        c.send(address[mac].encode())
    except KeyError:
        c.send("Not Found".encode())
~~~
*client.py*
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac=input("Enter logical address: ")
    s.send(mac.encode())
    print("MAC Address",s.recv(1024).decode())
~~~
## OUPUT -RARP

# SERVER 
![434650354-c0f45d88-03c6-4cb4-a30e-2d87afab6d7b](https://github.com/user-attachments/assets/3cb51c57-0481-43ac-a06d-96c1d72c2d01)

# CLIENT
![434650456-fdac2886-4459-4d9d-8a7f-2d673b7a9bde](https://github.com/user-attachments/assets/a6b980a8-d6b4-4204-97d3-c3f14a95bab5)

## RESULT
Thus, the python program for simulating ARP / RARP protocols using TCP was successfully 
executed.
