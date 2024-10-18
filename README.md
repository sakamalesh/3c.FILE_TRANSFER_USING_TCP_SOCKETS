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
## CLIENT:
'''

      import socket
      s=socket.socket()
      host=socket.gethostname()
      port=60000
      s.connect((host,port))
      s.send("Hello Server.".encode())
      with open('received_file','wb') as f:
          print('receiving Data....')
          while True:
              
              data=s.recv(1024)
              print('data=%s',(data))
              if not data:
                  break
              f.write(data)
      
      print("Successfully got the file")
      s.close()
      print('connection closed')

'''
## SERVER:
'''

    import socket
    port=60000
    s=socket.socket()
    host=socket.gethostname()
    s.bind((host,port))
    s.listen(5)
    print("server listening on port",port)
    while True:
        conn,addr=s.accept()
        print("Connected to",addr)
        data=conn.recv(1024)
        print("Server received",repr(data))
        filename='txt1.txt'
        with open(filename,'rb')as f:
            l=f.read(1024)
            while(l):
                conn.send(l)
                print('sent',repr(l))
                l=f.read(1024)
    
    print("Done Sending")
    conn.send("Thankyou for Connecting".encode())
    conn.close()

'''
## OUPUT
## SERVER:
![Screenshot 2024-10-17 111505](https://github.com/user-attachments/assets/930858c3-0b82-4f8a-b50e-1c44cf7928d9)

## CLIENT:
![Screenshot 2024-10-17 111457](https://github.com/user-attachments/assets/94c2faa2-b721-4ee8-9c91-bef8e02a12d3)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
