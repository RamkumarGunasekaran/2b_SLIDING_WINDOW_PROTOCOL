# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program for Implementation of sliding Window Protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUPUT
## Client:
![365878255-23e90014-9169-4b81-bb9a-3e756674bcd7](https://github.com/user-attachments/assets/60b52a05-a87c-4b0a-a8ae-1addf335f336)

## Server:
![365878334-a99c14a1-c71f-4813-a506-4f4a70aed92f](https://github.com/user-attachments/assets/de24693c-b058-4d86-afe4-18df76ec0c00)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
