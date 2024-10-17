# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM :

## Client.py :

```python
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
        print('data=%s' % data)
        if not data:
            break
        f.write(data)

f.close()
print('Successfully got the file')
s.close()
print('Connection closed')

```

## OUPUT :

![image](https://github.com/user-attachments/assets/5ce207f6-b440-45a7-b769-2c374e8c6454)

## Server.py :

```python
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
   filename=r"C:\Users\kiran\Desktop\sample.txt"
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

## Output :

![image](https://github.com/user-attachments/assets/29ba2e9d-18b8-4f18-be4c-62d47231de08)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
