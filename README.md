# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
SERVER:
'''
import socket
import os

HOST = '127.0.0.1'  
PORT = 65432  

def send_file(filename, conn):
    if os.path.isfile(filename):
        conn.sendall(b'EXISTS')
        file_size = os.path.getsize(filename)
        conn.sendall(str(file_size).encode('utf-8'))
        client_response = conn.recv(1024).decode('utf-8')
        if client_response == 'READY':
            with open(filename, 'rb') as f:
                chunk = f.read(1024)
                while chunk:
                    conn.sendall(chunk)
                    chunk = f.read(1024)
            print(f"File '{filename}' sent successfully.")
    else:
        conn.sendall(b'NOT_EXISTS')

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server_socket:
    server_socket.bind((HOST, PORT))
    server_socket.listen()

    print(f"File server is listening on {HOST}:{PORT}")
    while True:
        conn, addr = server_socket.accept()
        with conn:
            print(f"Connected by {addr}")

            filename = conn.recv(1024).decode('utf-8')
            print(f"Client requested file: {filename}")

            send_file(filename, conn)'''
client:
'''

import socket
import os

HOST = '127.0.0.1'  
PORT = 65432  

def send_file(filename, conn):
    if os.path.isfile(filename):
        conn.sendall(b'EXISTS')
        file_size = os.path.getsize(filename)
        conn.sendall(str(file_size).encode('utf-8'))
        client_response = conn.recv(1024).decode('utf-8')
        if client_response == 'READY':
            with open(filename, 'rb') as f:
                chunk = f.read(1024)
                while chunk:
                    conn.sendall(chunk)
                    chunk = f.read(1024)
            print(f"File '{filename}' sent successfully.")
    else:
        conn.sendall(b'NOT_EXISTS')

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server_socket:
    server_socket.bind((HOST, PORT))
    server_socket.listen()

    print(f"File server is listening on {HOST}:{PORT}")
    while True:
        conn, addr = server_socket.accept()
        with conn:
            print(f"Connected by {addr}")

            filename = conn.recv(1024).decode('utf-8')
            print(f"Client requested file: {filename}")

            send_file(filename, conn)'''
            
## OUPUT
![373116007-d5c23fe7-ec01-4ad0-ae8b-57f202cfcb71](https://github.com/user-attachments/assets/0a7bb4f0-89d1-4548-987f-df59f9179e8d)
![373116133-f413f5ab-5ca4-42b2-b8e8-299d6de1ad0e](https://github.com/user-attachments/assets/9fc1977f-f19b-4ac0-8b4e-be13b101c7b7)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
