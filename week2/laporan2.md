# MODUL 3
## Modul 3.2
Pada week 2 tetap melanjutkan materi pada modul 3 yaitu HTTP tetapi pada bagian ini akan membahas hal lain yaitu Basic HTTP GET/response interaction.

## Langkah-langkah percobaan
1. Membuka aplikasi wireshark terlebih dahulu
[tampilan](../assets/image/week1%20Download%20(7).png)

2. jika sudah membuka wireshark lanjut dengan memilih bagian WIFI untuk melakukan proses capture packet
[tampilan](../assets/image/week1%20Mod%203%20(2).png)

3. Pastikan sudah start capture dan langkah selanjutnya membuka browser http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
[tampilan](../assets/image/week2%20mod3.2.png)

4. Gunakan cara seperti pada week sebelumnya yaitu bagian untuk filter atau mencari HTTP
[tampilan](../assets/image/week1%20Mod%203%20(3).png)

5. Stop capture dan pada paket yang di pilih akan muncul rincian pesan
[tampilan](../assets/image/week2%20mod3.2%20(2).png)

## Uji coba Web not found
pada percobaan ini hanya sekedar uji coba bagaimana jika mencari menggunakan alamat web yang bisa di bilang asal saja tetapi tetap menggunakan HTTP

## Langkah-langkah percobaan
1. Buka aplikasi wireshark dan pilih WIFI lalu lakukan proses capture packet
[tampilan](../assets/image/week1%20Mod%203%20(2).png)

2. Lakukan filter untuk mencari HTTP
[tampilan](../assets/image/week1%20Mod%203%20(3).png)

3. Untuk langkah selanjutnya saya akan mencoba menggunakan link yang menggunakan HTTP tetapi link tersebut saya tambahkan beberapa huruf acak hanya untuk uji coba, saya menggunakan link http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.htmlregergev
[tampilan](../assets/image/web%20not%20found.png)

4. Setelah search link tersebut bisa buka wireshark lagi pada bagian HTTP akan muncul keterangan 404 atau eror
[tampilan](../assets/image/web%20not%20found%20(2).png)

# Modul 3.3
Pada modul ini berfokus pada Retrieving Long Document secara singkatnya proses mengambil data berukuran besar (seperti file, halaman web, atau dokumen panjang) dari hasil capture paket jaringan yang dikirim melalui protokol seperti HTTP, TCP, atau FTP.

## Langkah-langkah percobaan 
1. Buka aplikasi wireshark dan pilih WIFI lalu lakukan proses capture packet
[tampilan](../assets/image/week1%20Mod%203%20(2).png)
