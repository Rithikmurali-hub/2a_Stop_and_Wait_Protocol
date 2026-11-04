# 2a_Stop_and_Wait_Protocol
## NAME: Rithik M
## REG NO: 212225040342
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```


## OUTPUT
server.py

<img width="937" height="330" alt="Screenshot 2026-11-04 101339" src="https://github.com/user-attachments/assets/8e42bfe0-5b25-476d-9e48-a60b72c4d0b6" />

client.py
<img width="937" height="330" alt="Screenshot 2026-11-04 101339" src="https://github.com/user-attachments/assets/bed72e76-dd82-424a-9bc3-1f26c72c62eb" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
