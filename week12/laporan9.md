# MODUL 12  ICMP
ICMP adalah singkatan dari Internet Control Message Protocol, yaitu protokol jaringan yang digunakan untuk mengirim pesan kontrol dan informasi kesalahan dalam komunikasi data di internet.

ICMP bekerja bersama protokol IP untuk membantu:

- mengecek koneksi jaringan
- melaporkan error
- melakukan diagnosa jaringan

Contoh penggunaan ICMP:

- Ping
Menggunakan ICMP Echo Request dan Echo Reply untuk mengecek apakah suatu host aktif.
- Traceroute
Membantu mengetahui jalur paket data menuju tujuan.
- Pesan Error
Misalnya “Destination Unreachable” ketika alamat tujuan tidak bisa dicapai.

Struktur dasarnya biasanya terdiri dari:
- Type
- Code
- Checksum
- Data

ICMP tidak digunakan untuk mengirim data aplikasi seperti HTTP atau FTP, melainkan khusus untuk komunikasi kontrol jaringan.

## Langkah-Langkah Percobaan
1. Buka wireshark lalu pilih wifi
2. Buka CMD, kemudian ketikan perintah ping -n 10 www.ust.hk
![tampilan](../assets/image/week12(1).png)

3. Stop capture pada wireshark

4. Lakukan filter ICMP

5. Pilih dan expand salah satu paket ICMP Echo Reply
![tampilan](../assets/image/week12(2).png)

6. Pilih dan expand salah satu paket ICMP Echo Request
![tampilan](../assets/image/week12(3).png)

## Analisis 
- Pesan ICMP yang dihasilkan program Ping
![tampilan](../assets/image/week12(2).png)
Program ping pada percobaan ini menghasilkan dua jenis pesan ICMP, yaitu ICMP Echo Request dan ICMP Echo Reply. Terlihat pada Wireshark bahwa perangkat dengan IP 192.168.0.104 mengirimkan paket Echo Request ke alamat tujuan 143.89.209.9, kemudian server tujuan membalas dengan Echo Reply sebagai tanda koneksi berhasil dilakukan. Pada percobaan ini dilakukan ping sebanyak 10 kali sehingga muncul total 20 paket ICMP, terdiri dari 10 request dan 10 reply. Dari hasil tersebut dapat diketahui bahwa komunikasi jaringan berjalan dengan baik karena setiap request mendapatkan balasan dari host tujuan.

# Isi pesan
- ICMP Echo Request
![tampilan](../assets/image/week12%20(4).png)
Pada paket ICMP Echo Request terlihat bahwa perangkat dengan IP 192.168.0.104 mengirimkan permintaan ping ke alamat 143.89.209.9. Paket ini digunakan untuk mengecek apakah host tujuan dapat dijangkau melalui jaringan.

- Type = 8 → menunjukkan paket merupakan Echo Request atau permintaan ping
- Code = 0 → menandakan tidak ada error tambahan pada pesan ICMP
- Checksum = 0x4d5a [correct] → checksum valid sehingga paket dikirim tanpa kerusakan data
- Identifier = 1 (0x0001) → digunakan sebagai penanda agar paket reply dapat dikenali sebagai pasangan request yang sama
- Sequence Number = 1 (0x0001) → menunjukkan bahwa paket ini merupakan urutan ping pertama yang dikirim
- Request frame = 1984 → menandakan balasan reply nantinya terhubung dengan frame request ini

- ICMP Echo Reply
![tampilan](../assets/image/week12%20(5).png)
Pada paket ICMP Echo Reply terlihat bahwa host tujuan 143.89.209.9 memberikan balasan ke perangkat 192.168.0.104. Balasan ini menunjukkan bahwa koneksi jaringan berhasil dan perangkat tujuan dapat merespons permintaan ping.

- Type = 0 → menunjukkan paket merupakan Echo Reply atau balasan ping
- Code = 0 → tidak terdapat informasi error pada paket balasan
- Checksum = 0x555a [correct] → checksum valid sehingga data reply diterima dengan baik
- Identifier = 1 (0x0001) → identifier sama dengan request agar sistem dapat mencocokkan balasan dengan permintaan sebelumnya
- Sequence Number = 1 (0x0001) → menunjukkan bahwa paket reply ini merupakan balasan untuk request urutan pertama
- Request frame = 1978 → menunjukkan paket reply ini merupakan balasan dari frame request nomor 1978
- Response time = 78,584 ms → waktu yang dibutuhkan sejak request dikirim hingga reply diterima kembali oleh pengirim


# Analisis ICMP yang Dihasilkan Oleh Traceroute
1. Bukak wireshark dan pilih salah satu jaringan (Wifi), lalu aktifkan / capture

2. Buka CMD, kemudian ketikan perintah tracert www.ust.hk
![tampilan](../assets/image/week12%20analisis.png)

3. Stop capture pada wireshark

4. Lakukan filter ICMP

5. Pilih dan expand salah satu paket ICMP Echo Request

6. Pilih dan expand salah satu paket Time To Live (TTL)

- Pesan ICMP yang dihasilkan oleh program tracerout
![tampilan](../assets/image/week12%20analisis(2).png)
- ICMP Echo Request : Paket ini digunakan untuk meminta respon dari host atau router yang dilewati
- ICMP Time Exceeded (TTL Expired) : pesan yang dikirim oleh router ketika nilai TTL pada suatu paket habis sebelum paket mencapai tujuan

## Isi Pesan
- ICMP Echo Request
![tampilan](../assets/image/week12%20analisis(3).png)
Pada paket ICMP Echo Request terlihat bahwa perangkat dengan IP 192.168.0.104 mengirimkan permintaan ping ke alamat 143.89.209.9. Paket ini digunakan untuk mengecek koneksi dan memastikan host tujuan dapat dijangkau melalui jaringan.

- Type = 8 → menunjukkan paket merupakan Echo Request atau permintaan ping
- Code = 0 → tidak terdapat informasi error tambahan pada paket ICMP
- Checksum = 0xf7f2 [correct] → checksum valid sehingga paket tidak mengalami kerusakan saat transmisi
- Identifier = 1 (0x0001) → digunakan sebagai penanda paket request
- Sequence Number = 12 (0x000c) → menunjukkan bahwa paket ini merupakan urutan ping ke-12
- No response seen → menandakan belum terlihat balasan langsung untuk paket request ini pada capture

- ICMP Time Exceeded
![tampilan](../assets/image/week12%20analisis(4).png)
Pada paket ICMP Time Exceeded terlihat bahwa perangkat dengan IP 192.168.0.1 mengirimkan pesan ICMP error ke 192.168.0.104. Pesan ini muncul karena nilai TTL (Time To Live) pada paket habis sebelum mencapai tujuan akhir.

- Type = 11 → menunjukkan paket merupakan Time-to-live Exceeded
- Code = 0 → menandakan TTL exceeded in transit atau TTL habis di perjalanan
- Checksum = 0xf4ff [correct] → checksum valid sehingga paket diterima tanpa error
- Source IP = 192.168.0.1 → router/perangkat yang mengirim pesan TTL exceeded
- Destination IP = 192.168.0.104 → host pengirim traceroute atau ping
- Paket juga menampilkan kembali informasi Echo Request sebelumnya sebagai referensi paket yang mengalami TTL habis selama proses pengiriman data