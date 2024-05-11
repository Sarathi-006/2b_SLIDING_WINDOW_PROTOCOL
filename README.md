# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
##client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send: "))
l=list(range(size))
s=int(input("Enter Window Size: "))
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
##server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recieved from the server".encode())

```

## OUPUT
##client
<img width="936" alt="320746825-0e7e8ab7-69f6-49e5-8d82-89db3755fe13" src="https://github.com/Sarathi-006/2b_SLIDING_WINDOW_PROTOCOL/assets/149349756/43bb3e9f-9aff-4e7f-9033-7b04ee63d133">
##server
<img width="936" alt="320746837-bb3a9796-7101-484e-a259-b5ea603e8011" src="https://github.com/Sarathi-006/2b_SLIDING_WINDOW_PROTOCOL/assets/149349756/f5cef5c0-58f4-4555-89c2-a93aa28373d8">

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
