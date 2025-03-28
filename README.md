# 2a_Stop_and_Wait_Protocol

#### REG.NO:212223240177
#### NAME:VIGNESH R
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

### client.py
```py
import socket

# Create a socket
s = socket.socket()

# Connect to the server (localhost:8000)
s.connect(('localhost', 8000))

while True:
    # Receive data from server
    data = s.recv(1024).decode()
    if not data:
        break
    print("Received from Server:", data)

    # Send acknowledgment back to server
    s.send("Acknowledgement Received".encode())

# Close connection
s.close()

```

### server.py
```py
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
while True:
    i = input("Enter a data: ")
    c.send(i.encode())  # Send data to client
    ack = c.recv(1024).decode()  # Receive acknowledgment from client
    if ack:
        print(ack)  # Print the acknowledgment
        continue
    else:
        c.close()   
        break

```
## OUTPUT
![Screenshot 2025-03-18 105347](https://github.com/user-attachments/assets/83bf783b-0935-4b9b-8875-d616745c83f2)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
