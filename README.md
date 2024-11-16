# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Name:E.Mythri
## Register no:212223240034
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

## Client.py
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
## Server.py
```
import socket
port=60000
s=socket.socket()
host=socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server listening on port", port)

while True:
 conn,addr=s.accept()
 print("Connected to",addr)

 data=conn.recv(1024)
 print('Server received', repr(data))

 filename='C:\\Users\\admin\\Desktop\\CN\\mytext.txt'
 with open(filename, 'rb') as f:
   l=f.read(1024)
   while l:
    conn.send(l)
    print('Sent', repr(l)) 
    l=f.read(1024)

print('Done sending') 
conn.send('Thank you for connecting'.encode())
conn.close()
```
## OUTPUT
## Client.py
![Screenshot 2024-10-03 115727](https://github.com/user-attachments/assets/58596f28-7e5d-4695-8f66-ff10c89f9044)

## Server.py
![Screenshot 2024-10-03 115739](https://github.com/user-attachments/assets/8ac50391-dbaa-4f0b-a210-9014de32fe6d)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
