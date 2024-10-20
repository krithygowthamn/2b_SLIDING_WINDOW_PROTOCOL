# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## Name: Gowtham N
## Reg No: 212222220013
## AIM
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
s.connect(('localhost',8000))
while True:
  print(s.recv(1024).decode())
  s.send("acknowledgement recived from the server".encode())
```
## Server:
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
## OUPUT
## Client:
![image](https://github.com/user-attachments/assets/dfd52204-43f8-4063-8564-dfd843190992)

## Server:
![image](https://github.com/user-attachments/assets/1b59dd59-e3e0-450a-8ceb-08202721aa58)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
