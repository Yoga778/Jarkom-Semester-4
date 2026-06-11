# MODUL 14 WIFI

## Pengertian singkat
IEEE 802.11 merupakan standar komunikasi jaringan nirkabel yang dikembangkan oleh Institute of Electrical and Electronics Engineers (IEEE). Standar ini menjadi dasar teknologi Wi-Fi dan mengatur proses pertukaran data pada jaringan WLAN (Wireless Local Area Network), terutama pada lapisan fisik (Physical Layer) dan lapisan pengendalian akses media (Media Access Control/MAC).

## Perbandingan Frekuensi Wi-Fi:

1. Frekuensi 2,4 GHz

- Kelebihan: Mampu menjangkau area yang lebih luas serta memiliki kemampuan yang cukup baik dalam menembus dinding maupun hambatan fisik lainnya.
- Kekurangan: Kecepatan transfer data cenderung lebih rendah dan lebih mudah mengalami interferensi karena banyak perangkat elektronik lain yang menggunakan frekuensi yang sama.

2. Frekuensi 5 GHz

- Kelebihan: Menawarkan kecepatan transfer data yang lebih tinggi dengan tingkat gangguan sinyal yang lebih rendah.
- Kekurangan: Cakupan sinyal lebih terbatas dan performanya dapat menurun ketika terhalang oleh dinding atau material padat lainnya.

Access Point (AP) berfungsi sebagai penghubung antara perangkat nirkabel dan jaringan kabel. Selain itu, perangkat ini juga berperan dalam memancarkan sinyal Wi-Fi sehingga pengguna dapat mengakses jaringan tanpa harus terhubung langsung menggunakan kabel, terutama pada area yang sulit dijangkau oleh instalasi jaringan kabel.


## Analisis Beacon Frame
Pada percobaan ini akan menggunakan file yang pernah digunakan pada pertemuan sebelumnya. Buka didalam wireshark file zip yang sudah di extract lalu ketik pada bagian filter wireshark: wlan.fc.subtype == 8 && wlan.fc.type == 0
![tampilan](../assets/image/Modul%2014.png)
Wireshark, Beacon Frame dikirimkan secara periodik setiap sekitar 8 milidetik. Tercatat bahwa aktivitas beaconing ini berlangsung selama 73 detik dengan total pengiriman sebanyak 2363 kali.

![tampilan](../assets/image/Modul%2014%20(2).png)
Berdasarkan hasil pengamatan pada detail paket Frame 3, diperoleh beberapa informasi penting mengenai karakteristik jaringan nirkabel yang digunakan.

- PHY Type (802.11b HR/DSSS) menunjukkan bahwa komunikasi berlangsung menggunakan standar IEEE 802.11b dengan metode modulasi High-Rate Direct Sequence Spread Spectrum (HR/DSSS) yang umum digunakan pada jaringan Wi-Fi generasi awal.
Short Preamble bernilai False, yang berarti frame menggunakan Long Preamble. Bagian preamble berfungsi untuk proses sinkronisasi antara pengirim dan penerima sebelum data ditransmisikan. Penggunaan long preamble biasanya dipilih untuk menjaga kompatibilitas dengan perangkat yang lebih lama.

- Pada bagian Channel dan Frequency, terlihat bahwa jaringan beroperasi pada Channel 6 dengan frekuensi 2437 MHz, yang termasuk dalam pita frekuensi 2,4 GHz.
Nilai Signal Strength tercatat sebesar -30 dBm, menunjukkan kualitas sinyal yang sangat baik karena semakin mendekati nol maka sinyal yang diterima semakin kuat. Sementara itu, Noise Level berada pada -100 dBm, yang mengindikasikan tingkat gangguan sinyal sangat rendah sehingga komunikasi data dapat berlangsung dengan lebih stabil.

- Analisis Tagged Parameters
Pada parameter SSID, teridentifikasi nama jaringan nirkabel yang digunakan, yaitu “30 Munroe St”.

- Bagian Supported Rates memperlihatkan daftar kecepatan transfer data dasar yang didukung oleh access point, yaitu 1 Mbps, 2 Mbps, 5,5 Mbps, dan 11 Mbps.
Selain itu, pada Extended Supported Rates terdapat informasi mengenai dukungan kecepatan tambahan yang lebih tinggi, mulai dari 6 Mbps hingga 54 Mbps, yang menunjukkan kompatibilitas perangkat dengan standar Wi-Fi yang lebih modern.

## Analisis Data Transfer 
Untuk menganalisis perpindahan data, diterapkan filter alamat IP server: Untuk menganalisis perpindahan data, diterapkan filter alamat IP server:
![tampilan](../assets/image/Analisis%20Data%20Transfer.png)

Hasil pengamatan menunjukkan adanya proses TCP Three-Way Handshake yang terdiri dari paket SYN, SYN-ACK, dan ACK sebagai tahap pembentukan koneksi antara klien dan server. Setelah koneksi berhasil dibuat, pada Frame 480 terlihat paket HTTP GET yang digunakan klien untuk meminta file /wireshark-labs/alice.txt dari server.

## Analisis Proses Association & Disassociation
- Association (Asosiasi) merupakan tahapan awal saat perangkat klien melakukan proses koneksi ke Access Point. Pada tahap ini, klien mengirimkan permintaan untuk bergabung ke jaringan nirkabel, kemudian Access Point memberikan respons yang menentukan apakah koneksi tersebut dapat diterima atau tidak.

- Disassociation (Disasosiasi) adalah proses berakhirnya hubungan antara klien dan Access Point. Pemutusan koneksi ini dapat terjadi karena permintaan dari perangkat klien, perpindahan ke Access Point lain saat roaming, atau karena Access Point memutus koneksi akibat kondisi tertentu seperti perubahan konfigurasi maupun kualitas sinyal yang tidak memadai.

Diterapkan ekspresi filter untuk melihat manajemen jabat tangan nirkabel:wlan.fc.type_subtype == 0

- expand paket awal
![tampilan](../assets/image/Analisis%20Proses%20Association%20&%20Disassociation.png)

- expand paket akhir
![tampilan](../assets/image/Analisis%20Proses%20Association%20&%20Disassociation%20(2).png)

Berdasarkan perbandingan paket Association Request pada Frame 1750 dan Frame 2162, terdapat perubahan pada parameter SSID yang menunjukkan perpindahan koneksi jaringan oleh perangkat klien.

- Frame 1750:
Klien mengirimkan permintaan asosiasi ke Access Point dengan SSID "linksys_SES_24086". Hal ini menunjukkan bahwa perangkat sedang berusaha terhubung ke jaringan nirkabel tersebut.

- Frame 2162:
Klien mengirimkan permintaan asosiasi baru ke Access Point dengan SSID "30 Munroe St". Perubahan SSID ini menandakan bahwa perangkat telah beralih ke jaringan nirkabel yang berbeda.


Tanggapan Asosiasi (Association Response) dianalisis melalui filter subtype respon: wlan.fc.type_subtype == 1
![tampilan](../assets/image/Analisis%20Proses%20Association%20&%20Disassociation%20(3).png)

Frame 2166:
Pada frame ini teridentifikasi paket Association Response, yaitu respons dari Access Point terhadap permintaan asosiasi yang sebelumnya dikirim oleh klien. Nilai Transmitter Address menunjukkan MAC Address milik Access Point, yaitu CiscoLinksys_f7:1d:51, yang bertindak sebagai pengirim paket respons. Paket ini menandakan bahwa permintaan koneksi dari perangkat klien Intel_d1:6b:4f telah diterima dan disetujui, sehingga proses asosiasi berhasil dilakukan dan klien dapat melanjutkan komunikasi melalui jaringan nirkabel tersebut.