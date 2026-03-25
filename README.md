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
1. server.py
```
import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind
host = '127.0.0.1'
port = 12345
server_socket.bind((host, port))

# Listen
server_socket.listen(1)
print("Server waiting for connection...")

# Accept connection
conn, addr = server_socket.accept()
print("Connected to:", addr)

# Open file in binary mode
file = open("sample.txt", "rb")

# Read and send file data
data = file.read(1024)
while data:
    conn.send(data)
    data = file.read(1024)

print("File sent successfully!")

# Close
file.close()
conn.close()
server_socket.close()
```
2. client.py
```
import socket

# Create socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
host = '127.0.0.1'
port = 12345
client_socket.connect((host, port))

# Open file to write received data
file = open("received.txt", "wb")

# Receive file data
while True:
    data = client_socket.recv(1024)
    if not data:
        break
    file.write(data)

print("File received successfully!")

# Close
file.close()
client_socket.close()
```
## OUPUT
<img width="1052" height="59" alt="image" src="https://github.com/user-attachments/assets/19d36bb3-44ec-4c76-9827-5025900a99b1" />

<img width="1053" height="75" alt="image" src="https://github.com/user-attachments/assets/556fec0c-3ba4-494c-9613-ddd6527b069e" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
