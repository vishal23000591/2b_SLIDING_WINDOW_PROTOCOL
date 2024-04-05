# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program to implement the sliding window protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames:"))
l=list(range(size))
s=int(input("Enter window size:"))
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
## Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement Received from the server".encode())
```

## OUTPUT
![Screenshot 2024-04-05 104135](https://github.com/vishal23000591/2b_SLIDING_WINDOW_PROTOCOL/assets/147139719/0374aac3-d662-4809-a22d-7a617ad95f9c)
![Screenshot 2024-04-05 104153](https://github.com/vishal23000591/2b_SLIDING_WINDOW_PROTOCOL/assets/147139719/6e10dfed-9713-4ebe-a1dd-ceda5bd76591)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
