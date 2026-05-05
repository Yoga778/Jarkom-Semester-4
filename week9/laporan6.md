# MODUL 9 Web server
Web server adalah bagian penting dalam sistem komunikasi berbasis internet. Fungsinya adalah menerima permintaan (request) dari klien, seperti browser, lalu memberikan tanggapan(response) berupa halaman web atau data yang diminta. Proses pertukaran data ini biasanya menggunakan protokol HTTP yang berjalan di atas TCP.

## Langkah - Langkah membuat web sederhana
1. Membuat file server.py
2. Tulis code
```
from socket import *
import threading

def handle_client(connectionSocket):
    try:
        #input user
        #decode = 10101010 -> "pesan"
        massage = connectionSocket.recv(1024).decode()

        #nampung req tipe file dari pengguna
        #massage = GET /index.html HTTP/1.1 
        fileName = massage.split()[1]
        print(fileName[1:])

        #membuka index.html serta menghilangkan /
        f = open(fileName[1:])

        #membaca file html 
        outputData = f.read()

        print("TEST"+fileName[1:])

        #kirim respon
        connectionSocket.send(
            "HTTP/1.1 200 OK\r\n\r\n".encode()
        )

        #kirim data
        connectionSocket.sendall(outputData.encode())

    except IOError:
        connectionSocket.send(
            "HTTP/1.1 404 NOT FOUND\r\n\r\n".encode()
        )

        #kirim data
        connectionSocket.send(
            "<h1>404 NOT FOUND</h1>".encode()
        )

        ##TUTUP KONEKSI
        connectionSocket.close()

serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', 6799))
serverSocket.listen(5)#DAPAT MENERIMA SEBANYAK 5 CLIENT
print("[SYSTEM] Server is Running Away....")


while True:
    connectionSocket, add = serverSocket.accept()

    #membuat thread dan target threadnya, beserta parameternya
    thread = threading.Thread(
        target=handle_client,
        args=(connectionSocket,)
    )
    thread.start()
```

3. Buat file index.html di folder yang sama
4. Isi dalam file tersebut

```
<html>
<head>
    <title>Test Server</title>
</head>
<body>
    <h1>Hello World!</h1>
    <p>Ini hasil server Python TCP</p>
</body>
</html>
```

5. Setelah itu jalankan file server tadi terlebih dahulu 
6. Buka browser ketikan URL: http://localhost:6799/Index.html
untuk menampilakn output yang di buat di file yang index.html
<img width="1919" height="1023" alt="week9" src="https://github.com/user-attachments/assets/362ceaf3-bb9f-4271-88ed-7acfeaae7026" />


7. Buka browser ketik URL: http://localhost:6799/loka.html
pada bagian ini akan muncul 404 atau eror karena file html tidak sesuai nama
<img width="1919" height="1032" alt="week9 (2)" src="https://github.com/user-attachments/assets/e877986d-a7eb-4869-b2cf-50f99c232949" />



# Latihan
## Langkah - Langkah
1. buat file server.py (saya menggunakan file yang sapa seperti di atas)

2. buat file index.html lalu ketik

```
<h1>hallow</h1>
```

3. setelah itu sama seperti proses sebelumnya yaitu menjalankan file server dulu lalu masukkan url yang sama seperti sebelumnya untuk memunculkan tampilan pada file index.html
<img width="1918" height="1029" alt="week9 (3)" src="https://github.com/user-attachments/assets/6c2bb77f-b9c8-4b7a-8f25-591661b85293" />
