# MODUL 6 TCP 

## 6.2 Menangkap Tansfer TCP dalam Jumlah Besar dari Komputer Pribadi ke remote server
## Langkah - Langkah percobaan
1. buka browser yang di gunakan lalu buka web http://gaia.cs.umass.edu/wireshark-labs/alice.txt, setelah itu save file yang tertera
![tampilan](../assets/image/week4.png)

2. Selanjutnya buka http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html.
![tampilan](../assets/image/week4%20(2).png)

3. Langkah selanjutnya setalah buka link tersebut yaitu upload file yang sudah di save pada langkah pertama lalu upload dan tampilan akan muncul seperti pada gambar
![tampilan](../assets/image/week4%20(3).png)

4. Stop wireshark dan lakukan filter "tcp"
![tampilan](../assets/image/week4%20(4).png)
Paket SYN digunakan untuk memulai koneksi TCP antara client dan server (proses three-way handshake), bukan untuk mengirim file. Proses ini memastikan bahwa koneksi siap digunakan sebelum data ditransfer. Setelah koneksi berhasil dibuat, data file akan dikirim dalam beberapa segmen kecil melalui TCP. Hal ini terjadi karena TCP membagi data menjadi bagian-bagian kecil agar pengiriman lebih efisien dan dapat dikontrol.

Selanjutnya, setelah proses upload selesai, server mengirimkan respon HTTP/1.1 200 OK. Pesan ini menandakan bahwa file telah berhasil diterima dan diproses oleh server. Setelah itu, halaman web menampilkan pesan “Congratulations” sebagai indikasi bahwa proses upload berhasil.
![tampilan](../assets/image/week4%20(5).png)

## Pertanyaan
1. IP dan port TCP komputer klien mencari data di filter "HTTP" dan pilih paket POST
![tampilan](../assets/image/Pertanyaan%201%20week4.png)

- IP SERVER: 192.168.0.104

- Port SERVER: 53901

2. IP dan port TCP server mencari data di filter "HTTP" dan pilih paket HTTP/1.1 200 OK
![tampilan](../assets/image/Pertanyaan%202%20week%204.png)

- IP SERVER: 128.119.245.12

- Port SERVER: 80

# Uji Coba dasar TCP

## Langkah - Langkah Percobaan
1. Download dan extrak file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip

2. Buka file yang sudah di extrak tadi di dalam wireshark
![tampilan](../assets/image/Uji%20Coba%20TCP.png)

## Pertanyaan 
1. Nomor urut SYN, mencari data di filter tcp.flags.syn == 1 && tcp.flags.ack == 0
![tampilan](../assets/image/Pertanyaan%201%20Uji%20coba%20tcp.png)


2. SYN-ACK, mencari data di filter tcp.flags.syn == 1 && tcp.flags.ack == 1
![tampilan](../assets/image/Pertanyaan%202%20Uji%20coba%20TCP.png)

- Nomor urut (sequence number) pada segmen SYN-ACK bernilai 0, sedangkan nilai acknowledgment adalah 1. Nilai acknowledgment tersebut berasal dari sequence number pada segmen SYN sebelumnya yang telah ditambahkan 1. Segmen ini dikenali sebagai SYN-ACK karena pada bagian TCP Flags terdapat flag SYN dan ACK yang aktif.


3. Sequence number POST, mencari data di filter tcp.port == 1161 && tcp contains "POST"
![tampilan](../assets/image/Pertanyaan%203%20Uji%20coba%20TCP.png)


4. 6 segmen pertama + RTT
![tampilan](../assets/image/Pertanyaan%204%20Uji%20coba%20TCP.png)

- Nilai RTT diperoleh dari selisih waktu antara pengiriman segmen TCP dan diterimanya acknowledgment. Berdasarkan grafik Round Trip Time pada gambar, nilai RTT berada pada kisaran sekitar 90 ms hingga 280 ms. Nilai RTT tersebut mengalami fluktuasi yang cukup stabil, yang menunjukkan bahwa kondisi jaringan selama proses pengiriman data berubah-ubah namun masih dalam rentang yang relatif konsisten.


5. Panjang 6 segmen
![tampilan](../assets/image/Pertanyaan%205%20Uji%20coba%20TCP.png)

- total panjang dari 6 segmen adalah 7.865 byte


6. Buffer receiver


![tampilan](../assets/image/Pertanyaan%206%20Uji%20coba%20TCP.png)


7. Retransmission
- Tidak ditemukan Retransmission, bisa di lihat saat pada wireshark tidak ada label “TCP Retransmission”


8. ACK behavior
![tampilan](../assets/image/Pertanyaan%208%20Uji%20coba%20TCP.png)

- Jumlah data yang di-ACK tidak tetap dan bisa banyak. Penerima dapat mengakui beberapa segmen sekaligus, tidak selalu satu per satu

9. Thoroughtput
![tampilan](../assets/image/Pertanyaan%209%20Uji%20coba%20TCP.png)
buatkan pernyataan seperti itu dari gambar yang saya kirim

- Throughput merupakan jumlah data yang berhasil ditransmisikan dalam satuan waktu tertentu. Berdasarkan grafik throughput pada gambar, kecepatan transfer awalnya meningkat secara bertahap dari nilai rendah hingga mencapai kisaran sekitar 200 kbps hingga 260 kbps. Setelah itu, throughput terlihat relatif stabil meskipun terdapat fluktuasi kecil selama proses pengiriman data. Hal ini menunjukkan bahwa koneksi TCP mampu mempertahankan performa yang cukup konsisten selama transfer berlangsung.

# Congestion Control pada TCP

## Langkah - Langkah Perocbaan dan pertanyaan
1. Identifikasi Slow Start & Congestion Avoidance (file tcp-ethereal-trace-1)
- Buka file tcp-ethereal-trace-1 dengan wireshark lalu setelah membuka file dalam wireshark filter "TCP"
- Klik Statistics -> TCP Stream Graph -> Time-Sequence Graph (Stevens)

![tampilan](../assets/image/Control%20pada%20tcp.png)

- Di awal (0–±1 detik) grafik naik cepat, itu fase slow start. Setelah itu berubah jadi naik lebih pelan dan stabil (linear), tandanya masuk congestion avoidance. Grafiknya juga tidak terlalu stabil, kemungkinan karena delay/ACK, tapi secara keseluruhan masih stabil karena tidak ada penurunan tajam.

2. Identifikasi Slow Start & Congestion Avoidance (alice.txt)
- Buka Wireshark lalu pilih opsi wifi dan start
- Pada bagian ini sama seperti step yang sudah pernah di lakukan yaitu upload file "alice.txt" ke web http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html
- Buka wireshark lalu filter "TCP"

![tampilan](../assets/image/control%20pada%20tcp%20(2).png)

- Pada grafik kedua, kenaikan sequence number di awal tidak menunjukkan pola yang signifikan dan cenderung datar dalam beberapa waktu. Setelah itu, terjadi peningkatan secara tiba-tiba, sehingga fase slow start tidak terlihat jelas seperti pada grafik sebelumnya.

Perubahan berikutnya juga tidak menunjukkan pola linear yang stabil, melainkan berupa lonjakan-lonjakan. Hal ini mengindikasikan bahwa proses pengiriman data kurang konsisten kemungkinan dipengaruhi oleh variasi delay pada jaringan Wi-Fi. Meskipun demikian, koneksi masih tergolong stabil karena tidak terdapat penurunan drastis pada sequence number yang menandakan packet loss besar atau timeout.