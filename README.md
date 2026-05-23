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
Client
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print("Receiving data...")
        data = s.recv(1024)
        print("data =", data)
        if not data:
            break
        f.write(data)
print("Successfully got the file")
s.close()
print("Connection closed")
```
Server
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.bind((host, port))
s.listen(5)
print("Server listening...")
while True:
    conn, addr = s.accept()
    print("Connected to:", addr)
    data = conn.recv(1024)
    print("Server received:", repr(data))
    filename = 'mytext.txt'
    f = open(filename, 'rb')
    l = f.read(1024)
    while l:
        conn.send(l)
        print("Sent:", repr(l))
        l = f.read(1024)
    f.close()
    print("Done sending")
    conn.close()
```
## OUPUT
Client

<img width="1684" height="350" alt="image" src="https://github.com/user-attachments/assets/8caf6c10-00a1-4095-a1df-92577440782d" />

Server

<img width="1688" height="123" alt="image" src="https://github.com/user-attachments/assets/064438ba-8741-4802-8c4f-8acf54e6a0b2" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
