# 3b) CREATION OF CHAT USING TCP SOCKETS

## AIM
To write a Python program for creating a Chat application using TCP sockets.

## ALGORITHM
1. Import the `socket` module in Python.
2. Create a TCP socket in the server, bind it to the host and port, listen for connections and accept the client.
3. Create a TCP socket in the client and connect it to the server's host and port.
4. The client reads a message from the user and sends it to the server using `sendall()`.
5. The server receives and displays the client's message, then reads a reply from the user and sends it back.
6. The client receives and displays the server's reply.
7. Repeat steps 4 to 6 until the client types `exit`, then close the sockets.

## PROGRAM

### Client
```python
import socket

with socket.socket() as s:
    s.connect(('localhost', 8000))
    while (msg := input("Client > ")) != "exit":
        s.sendall(msg.encode())
        print("Server >", s.recv(1024).decode())
```

### Server
```python
import socket

with socket.socket() as s:
    s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    s.bind(('localhost', 8000))
    s.listen(5)
    c, addr = s.accept()
    with c:
        while data := c.recv(1024):
            print("Client >", data.decode())
            c.sendall(input("Server > ").encode())
```

## OUTPUT
Refer to the following screenshot to view the output of the program.
<img width="836" height="112" alt="image" src="https://github.com/user-attachments/assets/9af74941-a1a9-4b3c-98f6-bef9411225d3" />

<img width="841" height="128" alt="image" src="https://github.com/user-attachments/assets/294d5c9e-fe50-4744-93f0-72d823bfad61" />


## RESULT
Thus, the Python program for creating a Chat application using TCP sockets was successfully created and executed.
