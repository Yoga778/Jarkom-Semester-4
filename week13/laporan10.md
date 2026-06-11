# MODUL13 ARP
ARP (Address Resolution Protocol) merupakan protokol jaringan yang berfungsi untuk menghubungkan atau mengonversi alamat IP menjadi MAC Address dalam jaringan lokal (LAN). Protokol ini dibutuhkan karena proses komunikasi pada lapisan Data Link menggunakan MAC Address sebagai identitas perangkat, sementara pengguna biasanya mengenali perangkat berdasarkan alamat IP yang dimiliki

## Cara kerja ARP
1. Perangkat akan memulai proses pengiriman data ke alamat IP tujuan yang berada dalam jaringan lokal yang sama.
2. Sebelum mengirim data, perangkat terlebih dahulu mengecek ARP Cache untuk mengetahui apakah informasi pasangan alamat IP dan MAC Address tujuan sudah tersedia.
3. Jika data tersebut belum ditemukan, perangkat akan mengirimkan ARP Request ke seluruh perangkat dalam jaringan menggunakan metode broadcast.
4. Perangkat yang memiliki alamat IP yang sesuai akan merespons dengan ARP Reply yang berisi MAC Address miliknya.
5. Informasi pasangan alamat IP dan MAC Address yang diterima kemudian disimpan ke dalam ARP Cache agar dapat digunakan kembali pada komunikasi berikutnya.
6. Setelah alamat MAC tujuan berhasil diketahui, proses pengiriman data ke perangkat tujuan dapat dilakukan.

## Langkah-Langkah Percobaan
1. Buka CMD sebagai administrator lalu jalankan perintah: arp -d * untuk menghapus seluruh isi ARP Cache, sehingga komputer harus melakukan proses ARP kembali ketika ingin berkomunikasi dengan perangkat lain
![tampilan](../assets/image/Modul%2013.png)

2. Membuka Wireshark lalu memilih Analyze -> Enabled Protocols -> IPv4
![tampilan](../assets/image/Modul%2013%20(2).png)

3. Buka wireshark lalu Start capture pada wireshark

4. Buka browser lalu akses link berikut: http://gaia.cs.umass.edu/wireshark-labs/HTTP-ethereal-lab-file3.html

5. Setelah membuka link tersebut Stop capture pada wireshark

6. Pada bagian filter wireshark ketik ARP
![tampilan](../assets/image/Modul%2013%20(3).png)

7. Pilih salah satu paket untuk di analisis 
![tampilan](../assets/image/Modul%2013%20(4).png)

Berdasarkan hasil capture Wireshark, paket yang diamati merupakan ARP Request yang dikirim oleh perangkat dengan IP 192.168.0.1 dan MAC Address 84:d8:1b:a5:7f:ce untuk mencari MAC Address dari perangkat yang memiliki IP 192.168.0.100, sehingga karena alamat MAC tujuan belum diketahui maka kolom Target MAC Address masih bernilai 00:00:00:00:00:00 dan paket dikirim secara broadcast ke alamat ff:ff:ff:ff:ff:ff agar dapat diterima oleh seluruh perangkat dalam jaringan lokal, lalu perangkat yang memiliki IP tersebut akan membalas dengan ARP Reply yang berisi MAC Address miliknya sehingga komunikasi data dapat dilakukan ke tujuan yang benar.