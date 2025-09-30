# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a python program to perform Sliding Window Protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
# Client:
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
# Server:
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode()) 
```
## OUPUT:
# Client:
<img width="657" height="261" alt="image" src="https://github.com/user-attachments/assets/3df986f6-dcc9-4129-a835-a54b7a019d2a" />

# Server:
<img width="657" height="189" alt="image" src="https://github.com/user-attachments/assets/ee9f0e45-7ff1-479a-bf69-f7b68b72b757" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
