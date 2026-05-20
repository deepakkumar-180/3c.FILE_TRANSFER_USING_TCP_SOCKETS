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

<h1>server</h1>

```

import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(1)
print("Server listening...")
conn, addr = s.accept()
print("Connected by:", addr)
msg = conn.recv(1024).decode()
print("Client Message:", msg)
filename = "sample.txt"
with open("deepak.py", "rb") as f:
    data = f.read(1024)
    while data:
        conn.send(data)
        data = f.read(1024)
print("File sent successfully")
conn.close()
s.close()

```

<h2>client</h2>

```

import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello Server!".encode())
with open("received_file.txt", "wb") as f:
    while True:
        print("Receiving data...")
        data = s.recv(1024)
        if not data:
            break
        print("Data received:", data)
        f.write(data)
print("File received successfully")
s.close()
print("Connection closed")

```

## OUTPUT

<img width="848" height="282" alt="Screenshot 2026-05-20 132113" src="https://github.com/user-attachments/assets/a0893494-e97e-4c3d-98b6-1b160c046e3c" />
<img width="845" height="702" alt="Screenshot 2026-05-20 132050" src="https://github.com/user-attachments/assets/f2f0e01e-ebf4-41d1-a7ce-b99228cefd85" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
