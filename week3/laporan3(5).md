# MODUL 5 UDP


## Langkah - Langkah Percobaan
1. Download file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip

2. Extract file yang sudah di download sebelumnya
![tampilan](../assets/image/MOD%205.png)

3. Setelah extract click file tersebut untuk di buka di wireshark, setelah itu pada bagian filter ketik UDP untuk mengfilter.
![tampilan](../assets/image/MOD%205%20(2).png)

## Pertanyaan
1. Field UDP
![tampilan](../assets/image/MOD%205%20Pertanyaan%201.png)

Pada percobaan terdapat 4 field yang tersedia: Source port, Destination port, Lenght, Checksum

2. Panjang masing - masing dari dari field yang ada pada soal 1 yaitu :
- Source port: 2 byte
- Destination port: 2 byte
- Lenght: 2 byte
- Checksum: 2 byte 
- di karenakan Header UDP selalu memiliki ukuran tetap 8 byte dan pada percobaan di atas ada 4 field jadi setiap field memiliki panjang 2 byte

3. Lenght

![tampilan](../assets/image/Pertantaan%203%20MOD%205.png)

Pada gambar yang tertera terlihat bahwa Lenght memiliki panjang 58 yang artinya UDP Payload + Header UDP = 50 + 8 = 58, dan di dapatkan UDP Lenght 58 itu. Jadi, nilai “Length” benar menunjukkan ukuran keseluruhan paket UDP (header + payload).

4. Jumlah maksimum byte UDP 
- Field Length pada UDP menggunakan ukuran 16 bit (2 byte), sehingga nilai maksimalnya adalah:
- 2 − 1 = 65.535 byte
- Karena Length = header (8 byte) + payload, maka:
- Payload maksimum = 65.535 − 8 = 65.527 byte

5. Nomor port terbesar yang dapat digunakan sebagai source port pada UDP adalah 65.535, karena field port pada UDP berukuran 16 bit sehingga nilai maksimumnya adalah 2^16 − 1.

6. Berdasarkan bagian “Protocol” pada header IP di gambar (terlihat Protocol: UDP (17)), maka:
- Nomor protokol untuk UDP adalah 17 dalam desimal, yang dalam notasi heksadesimal ditulis sebagai 0x11.
![tampilan](../assets/image/Pertanyaan%206%20UDP.png)

7. Hubungan port
![tampilan](../assets/image/Pertanyaan%207%20UDP%20(1).png) 
![tampilan](../assets/image/Pertanyaan%207%20UDP%20(2).png) 

- Berdasarkan gambar:

- Paket 1 (request):
Source Port = 4334, Destination Port = 161

- Paket 2 (reply):
Source Port = 161, Destination Port = 4334

- Hubungannya adalah nomor port pada paket kedua merupakan kebalikan (ditukar) dari paket pertama, yaitu source port menjadi destination port, dan destination port menjadi source port.

- Jadi, dapat disimpulkan bahwa pada paket balasan UDP, port pengirim dan penerima saling bertukar posisi karena arah komunikasi juga berbalik.