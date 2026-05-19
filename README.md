# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
SERVER
```
import socket

port = 60000

s = socket.socket()

host = socket.gethostname()

s.bind((host, port))

s.listen(5)

print("Server listening...")

c, addr = s.accept()

print("Connected to", addr)

filename = "sample.txt"

with open(filename, 'rb') as f:

    data = f.read(1024)

    while data:

        c.send(data)

        data = f.read(1024)

print("File sent successfully")

c.close()

s.close()
```
CLIENT
```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file.txt', 'wb') as f:

    while True:

        print("receiving data...")

        data = s.recv(1024)

        print("data =", data)

        if not data:
            break

        f.write(data)

print("Successfully received the file")

s.close()

print("Connection closed")
```
## OUPUT
![alt text](image.png)
![alt text](image-1.png)
## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
