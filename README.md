# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Name : H Vishinu
## Reg No : 212223220124
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Client :
```
import socket

s = socket.socket()
port = 60000
s.connect(('localhost', port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s' % (data))
        if not data:
            break
        f.write(data)

print('Successfully get the file')
s.close()
print('connection closed')

```
Server :

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

    filename = 'myfile.txt'
    f = open(filename, 'rb')
    l = f.read(1024)
    while l:
        conn.send(l)
        print('Sent', repr(l))
        l = f.read(1024)
    f.close()

    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()


```


## OUPUT
Client :
![Screenshot 2024-04-22 202149](https://github.com/VisHinu24/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144244396/34c6e583-bbd3-4d2a-93db-a96da8370f40)

Server :
![Screenshot 2024-04-22 202158](https://github.com/VisHinu24/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144244396/33ab7668-2caa-47bf-948c-2053006903c5)


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
