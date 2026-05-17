# 2a_Stop_and_Wait_Protocol
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
Server Side:
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
s.close()

```

Client Side:

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
Server and Client:


<img width="252" height="147" alt="Screenshot 2026-05-13 152609" src="https://github.com/user-attachments/assets/d0084e99-5bb1-405d-8d0a-a542202d57e3" />
<img width="305" height="112" alt="Screenshot 2026-05-13 152623" src="https://github.com/user-attachments/assets/fa6585c8-5fe0-45a1-a8db-b907c13a677e" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
