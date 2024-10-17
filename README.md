# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
### Date:
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
##### Developed by: Ramya R
##### Register by: 212223230169
### SERVER
```
import socket                                                                           
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind((host, port)) 
s.listen(5) 
while True: 
conn, addr = s.accept() 
data = conn.recv(1024) 
print('Server received', repr(data)) 
filename='mytext.txt' 
f = open(filename,'rb') 
l = f.read(1024) 
while (l): 
conn.send(l) 
print('Sent ',repr(l)) 
l = f.read(1024) 
f.close() 
print('Done sending') 
conn.send('Thank you for connecting'.encode())
conn.close()
```
### CLIENT
```
import socket                                                                              
s = socket.socket() 
host = socket.gethostname() 
port = 60000 
s.connect((host, port)) 
s.send("Hello server!".encode()) 
with open('received_file', 'wb') as f: 
while True: 
print('receiving data...') 
data = s.recv(1024) 
print('data=%s', (data)) 
if not data: 
break 
f.write(data) 
f.close() 
print('Successfully get the file') 
s.close() 
print('connection closed')
```

## OUTPUT
### Client:
![client3c](https://github.com/VincyJovitha01/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147121113/019749c0-d616-478b-9d64-c6f6f554f9df)

### Server:
![server3c](https://github.com/VincyJovitha01/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147121113/0435a3d2-c768-4157-933a-af73ba1ffa3e)


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
