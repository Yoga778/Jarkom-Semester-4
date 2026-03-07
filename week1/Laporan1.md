# Laporan Praktikum Week 1 (Modul 2 & Modul 3)
Instalasi wireshark dan materi tentang HTTP

## Tujuan Praktikum
Mempelajari wireshark
Cara install wireshark
Belajar materi tentang HTTP

## Penjelasan singkat 
Wireshark adalah software untuk menganalisis lalu lintas jaringan (network traffic). Program ini dapat menangkap dan menampilkan paket data yang lewat di suatu jaringan secara detail.

Kegunaannya:
1. Menganalisis jaringan untuk melihat data yang dikirim dan diterima.
2. Troubleshooting jaringan (mencari penyebab jaringan lambat atau error).
3. Keamanan jaringan untuk mendeteksi aktivitas mencurigakan.
4. Pembelajaran jaringan untuk memahami cara kerja protokol seperti TCP, HTTP, DNS, dll

# Langkah Percobaan Modul 2 (Install wireshark)
1. Install wireshark melalui browser, pilih yang windows x64 installer (jika menggunakan windows)
![tampilan](../assets/image/Week1%20Download%20(1).png)

2. Jika suda lanjukan dengan click open file pada wireshark yang sudah di install tadi dan click next hingga complete
![tampilan](../assets/image/Week1%20Download%20(2).png)

![tampilan](../assets/image/Week1%20Download%20(3).png)

![tampilan](../assets/image/Week1%20Download%20(4).png)

 pada bagian ini user bisa memilih mau di letakkan dimana untuk wiresharknya
![tampilan](../assets/image/Week1%20Download%20(5).png)

![tampilan](../assets/image/Week1%20Download%20(6).png)

3. Jika sudah bisa langsunga buka wireshark dan akan muncul tampilan seperti pada gambar
![tampilan](../assets/image/week1%20Download%20(7).png)


# Langkah Percobaan Modul 3 (HTTP)
Pada modul ini mempelajari bagaimana cara mencari atau memfilter suatu protokol pada wireshark. Sebagain contoh, di sini ingin mencari protokol "HTTP" pada wireshark

## Langkah uji coba
1. Buka browser dan mengakses alamat web yang berbasis HTTP (contoh:http://gaia.cs.umass.edu/wireshark-labs/HTTPwireshark-file1.html)

 gambar setalah link tersebut di buka pada browser
![tampilan](../assets/image/week1%20Mod%203.png)

2. Buka wireshark, pada tampilan awal pilih wifi (jika menggunakan wifi semisal menggunakan LAN bisa pilih tulisan ethernet)
![tampilan](../assets/image/week1%20Download%20(7).png)

 Tampilan setelah memilih pilihan wifi
![tampilan](../assets/image/week1%20Mod%203%20(2).png)

3. jika sudah pada tampilan tersebut di bagian atas ada kolom yang bisa di gunakan untuk filter suatu protokol, pada kolom tersebut bisa ketik "HTTP" untuk mempermudah mencari protokol yang ingin di cari
![tampilan](../assets/image/week1%20Mod%203%20(3).png)

 Tmpilan setelah mencari protokol HTTP
![tampilan](../assets/image/week1%20Mod%203%20(4).png)

# Detail paket
Ketika salah satu paket dipilih wireshark akan menampilkan detail paket tersebut, contohnya "HTTP/1.1 200 OK
![tampilan](../assets/image/week1%20Mod%203%20(5).png)

![tampilan](../assets/image/week1%20Mod%203%20(6).png)
Status 200 OK menunjukkan bahwa permintaan (request) yang dikirim oleh komputer telah diterima dan diproses dengan baik oleh server. Pada bagian bawah, yaitu panel Packet Details, terlihat struktur protokol mulai dari lapisan fisik hingga lapisan aplikasi. Sementara itu, pada bagian Line-based text data, dapat dilihat isi HTML yang dikirim oleh situs tersebut, yaitu teks “Congratulations! You've downloaded the first Wireshark lab file!”. Hal ini menggambarkan bahwa data yang dikirim melalui internet dipecah menjadi beberapa paket sebelum akhirnya disusun kembali.