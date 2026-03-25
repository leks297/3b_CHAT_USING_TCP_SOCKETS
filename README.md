# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
## server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Server is listening...")
c, addr = s.accept()
print("Connected with", addr)

while True:
    ClientMessage = c.recv(1024).decode()

    if not ClientMessage or ClientMessage.lower() == 'exit':
        print("Client disconnected.")
        break

    print("Client >", ClientMessage)

    msg = input("Server > ")

    if msg.lower() == 'exit':
        c.send(msg.encode())
        break

    c.send(msg.encode())

c.close()
s.close()
```
## client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = input("Client > ")

    if msg.lower() == 'exit':
        s.send(msg.encode())
        break

    s.send(msg.encode())
    reply = s.recv(1024).decode()
    print("Server >", reply)

s.close()
```
## OUPUT
<img width="1268" height="320" alt="image" src="https://github.com/user-attachments/assets/e9daa4ef-4080-4bee-9b2d-6b2a954ed3ba" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
