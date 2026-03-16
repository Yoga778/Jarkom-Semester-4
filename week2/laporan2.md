# MODUL 3
## Modul 3.2 Basic HTTP GET/response interaction 
Pada week 2 tetap melanjutkan materi pada modul 3 yaitu HTTP tetapi pada bagian ini akan membahas hal lain yaitu Basic HTTP GET/response interaction.

## Langkah-langkah percobaan
1. Membuka aplikasi wireshark terlebih dahulu
![tampilan](../assets/image/week1%20Download%20(7).png)

2. jika sudah membuka wireshark lanjut dengan memilih bagian WIFI untuk melakukan proses capture packet
![tampilan](../assets/image/week1%20Mod%203%20(2).png)

3. Pastikan sudah start capture dan langkah selanjutnya membuka browser http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
![tampilan](../assets/image/week2%20mod3.2.png)

4. Gunakan cara seperti pada week sebelumnya yaitu bagian untuk filter atau mencari HTTP
![tampilan](../assets/image/week1%20Mod%203%20(3).png)

5. Stop capture dan pada paket yang di pilih akan muncul rincian paket
![tampilan](../assets/image/week2%20mod3.2%20(2).png)

## Uji coba Web not found
pada percobaan ini hanya sekedar uji coba bagaimana jika mencari menggunakan alamat web yang bisa di bilang asal saja tetapi tetap menggunakan HTTP

## Langkah-langkah percobaan
1. Buka aplikasi wireshark dan pilih WIFI lalu lakukan proses capture packet
![tampilan](../assets/image/week1%20Mod%203%20(2).png)

2. Lakukan filter untuk mencari HTTP
![tampilan](../assets/image/week1%20Mod%203%20(3).png)

3. Untuk langkah selanjutnya saya akan mencoba menggunakan link yang menggunakan HTTP tetapi link tersebut saya tambahkan beberapa huruf acak hanya untuk uji coba, Saya menggunakan link http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.htmlregergev
![tampilan](../assets/image/web%20not%20found.png)

4. Setelah search link tersebut bisa buka wireshark lagi pada bagian HTTP akan muncul keterangan 404 atau eror
![tampilan](../assets/image/web%20not%20found%20(2).png)


# Modul 3.3 Retrieving Long Documents 
Pada modul ini berfokus pada Retrieving Long Document secara singkatnya proses mengambil data berukuran besar (seperti file, halaman web, atau dokumen panjang) dari hasil capture paket jaringan yang dikirim melalui protokol seperti HTTP, TCP, atau FTP.

## Langkah-langkah percobaan 
1. Buka aplikasi wireshark dan pilih WIFI lalu lakukan proses capture packet
![tampilan](../assets/image/week1%20Mod%203%20(2).png)

2. Buka browser yang biasanya di gunakan lalu masukkan link ini: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
![tampilan](../assets/image/Retrieving%20Long%20Documents.png)

3. Gunakan filter HTTP pada wireshark untuk melihat paket HTTP
![tampilan](../assets/image/week1%20Mod%203%20(3).png)

4. Stop capture paket dan pilih salah satu paket untuk melihat isi dari paket tersebut secara detail
![tampilan](../assets/image/Retrieving%20Long%20Documents%20(2).png)


# Modul 3.4 HTML Documents dengan Embedded Objects
Pada modul ini mempelajari tentang HTML Documents dengan Embedded Objects dokumen pengertian singkatnya HTML yang memiliki objek tambahan di dalamnya seperti gambar, CSS, JavaScript, atau file lain, yang saat dibuka akan menyebabkan browser mengirim beberapa request HTTP yang dapat terlihat di Wireshark.

## Langkah-langkah percobaan
1. Buka aplikasi wireshark dan pilih WIFI lalu lakukan proses capture packet
![tampilan](../assets/image/week1%20Mod%203%20(2).png)

2. Buka browser yang biasanya di gunakan lalu masukkan link ini: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
![tampilan](..//assets/image/HTML%20Documents%20dengan%20Embedded%20Objects.png)

3. Setelah itu kembali ke wireshark dan gunakan filter HTTP pada wireshark untuk melihat paket HTTP
![tampilan](../assets/image/week1%20Mod%203%20(3).png)

4. Setelah membuka link tersebut di browser lalu cek di wireshark akan terlihat tulisan jpeg dikarenakan pada link tersebut saat di search terdapat gambar jadi pada wireshark menampilkan data atau menditeksi pada alamat tersebut terdapat gambar
![tampilan](../assets/image/HTML%20Documents%20dengan%20Embedded%20Objects%20(2).png)


# Modul 3.5 HTTP Authentication
Pada modul ini menjelaskan tentang HTTP Authentication secara singkatnya HTTP Authentication adalah proses autentikasi (login) yang terjadi saat client mengakses website yang membutuhkan username dan password, dan proses tersebut bisa terlihat di paket HTTP yang ditangkap oleh Wireshark.

## Langkah-langkah percobaan
1. Buka aplikasi wireshark dan pilih WIFI lalu lakukan proses capture packet
![tampilan](../assets/image/week1%20Mod%203%20(2).png)

2. Buka browser yang biasanya di gunakan lalu masukkan link ini: http://gaia.cs.umass.edu/wireshark-labs/protected_pages/HTTP-wireshark-file5.html
![tampilan](../assets/image/HTTP%20Authentication.png)
akan muncul perintah di minta untuk masukkan username dan password

3. Masukkan username: wireshark-students dan password: network, setelah masukkan password lalu tekan enter
![tampilan](..//assets/image/HTTP%20Authentication%20(2).png)

4. ketika berhasil pada wireshark akan muncul tulisan Unauthorized di salahsatu paket
![tampilan](..//assets/image/HTTP%20Authentication%20(3).png)
