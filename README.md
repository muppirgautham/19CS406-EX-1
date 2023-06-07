19CS406-EX-1 STUDY OF SOCKET PROGRAMMING WITH CLIENT-SERVER MODEL
DATE :09-03-2023

AIM :

To implement socket programming date and time display from client to server using TCPSockets

ALGORITHM :

Server:

Create a server socket and bind it to port.
Listen for new connection and when a connection arrives, accept it.
Send server‟s date and time to the client.
Read client‟s IP address sent by the client.
Display the client details.
Repeat steps 2-5 until the server is terminated.
Close all streams.
Close the server socket.
Stop.
Client:

Create a client socket and connect it to the server‟s port number.
Retrieve its own IP address using built-in function.
Send its address to the server.
Display the date & time sent by the server.
Close the input and output streams.
Close the client socket.
Stop
PROGRAM :

CLIENT :

import socket
from datetime import datetime
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
print("Client Address : ",addr)
now = datetime.now()
c.send(now.strftime("%d/%m/%Y %H:%M:%S").encode())
ack=c.recv(1024).decode()
if ack:
    print(ack)
c.close()
SERVER :

import socket
s=socket.socket()
s.connect(('localhost',8000))
print(s.getsockname())
print(s.recv(1024).decode())
s.send("acknowledgement recived from the server".encode())
OUTPUT: 
https://user-images.githubusercontent.com/119641638/239670072-ca9fb508-e605-4042-a02c-7f5800e40d6c.png

RESULT: 
Thus, the program to implement socket programming date and time display from client to server using TCP Sockets was successfully executed.
