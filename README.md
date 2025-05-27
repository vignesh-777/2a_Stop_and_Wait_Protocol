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

client_socket = socket.socket() 
client_socket.connect(('localhost', 8000)) 

while True: 
    print(client_socket.recv(1024).decode()) 
    client_socket.send("Acknowledgement Received".encode())

```

### server.py
```py
import socket 

server_socket = socket.socket() 
server_socket.bind(('localhost', 8000))
server_socket.listen(5) 

client_socket, client_address = server_socket.accept() 

while True: 
    user_input = input("Enter a data: ") 
    client_socket.send(user_input.encode()) 
    acknowledgement = client_socket.recv(1024).decode() 
    
    if acknowledgement: 
        print(acknowledgement) 
        continue 
    else: 
        client_socket.close() 
        break


```
## OUTPUT
![Screenshot 2025-03-18 105347](https://github.com/user-attachments/assets/83bf783b-0935-4b9b-8875-d616745c83f2)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
