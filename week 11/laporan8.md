# MODUL 11 DHCP
DHCP (Dynamic Host Configuration Protocol) adalah protokol jaringan yang digunakan untuk memberikan alamat IP secara otomatis kepada perangkat yang terhubung ke jaringan, seperti komputer, laptop, smartphone, atau printer.

## Fungsi DHCP
DHCP membantu administrator jaringan agar tidak perlu mengatur IP address secara manual pada setiap perangkat.

## Kelebihan DHCP
- Praktis dan otomatis
- Mengurangi konflik IP
- Memudahkan pengelolaan jaringan

## Kekurangan DHCP
- Bergantung pada DHCP Server
- Jika server mati, perangkat baru tidak mendapat IP

## DORA
DORA adalah singkatan dari Discover, Offer, Request, dan Acknowledgement, yaitu tahapan komunikasi pada protokol DHCP untuk memberikan alamat IP secara otomatis kepada perangkat dalam jaringan komputer.

Proses DORA terjadi ketika sebuah perangkat ingin terhubung ke jaringan tetapi belum memiliki IP address. Melalui tahapan ini, perangkat dapat memperoleh IP address beserta konfigurasi jaringan lainnya dari DHCP Server sehingga dapat digunakan untuk berkomunikasi dalam jaringan.

## Langkah-Langkah Percobaan
1. Download dan ekstrak file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
2. Setelah extrak buka file tersebut ke dalam wireshark dan gunakan filter dhcp untuk filter bagian dhcp saja
![tampilan](../Jarkom-Semester-4/assets/image/week11.png)

## Tahapan DORA pada DHCP

- Discover
Pada tahap pertama, client mengirimkan pesan DHCP Discover untuk mencari keberadaan DHCP server yang aktif di dalam jaringan. Alamat IP sumber masih menggunakan 0.0.0.0 karena client belum memperoleh IP address. Paket dikirim secara broadcast supaya semua DHCP server pada jaringan dapat menerima permintaan tersebut.

- Offer
Setelah menerima pesan Discover, DHCP server akan merespons dengan mengirimkan DHCP Offer. Pesan ini berisi penawaran alamat IP beserta informasi konfigurasi jaringan lain yang dapat digunakan oleh client, seperti subnet mask dan gateway.

- Request
Pada tahap berikutnya, client memilih salah satu penawaran IP dari server DHCP. Client kemudian mengirimkan DHCP Request sebagai bentuk permintaan sekaligus persetujuan terhadap alamat IP yang ditawarkan server.

- Acknowledgement (ACK)
Tahap terakhir adalah DHCP ACK yang dikirim oleh server DHCP kepada client. Pesan ini menandakan bahwa alamat IP telah resmi diberikan dan dapat digunakan oleh client untuk terhubung ke jaringan.
