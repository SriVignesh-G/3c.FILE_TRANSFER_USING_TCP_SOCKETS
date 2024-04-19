# Ex No:3c CREATION FOR FILE TRANSFER USING TCP SOCKETS
# Name: Sri Vignesh G
# Reg No: 212223040204

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### Client.py:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect(('localhost', port))
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
### Server.py:
```
import socket 
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind(('localhost', port)) 
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
## OUTPUT:
### Client Window:
![Screenshot 2024-04-19 234829](https://github.com/SriVignesh-G/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147576510/ad3f6a1a-3898-4d03-bf77-55f9a4e85924)

### Server Window:
![Screenshot 2024-04-19 234817](https://github.com/SriVignesh-G/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147576510/0aa34683-f69b-472b-b761-8015115e4453)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
