# MODUL 5 UDP


## Langkah - Langkah Percobaan
1. Download file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip

2. Extract file yang sudah di download sebelumnya
![tampilan](../assets/image/MOD%205.png)

3. Setelah extract click file tersebut untuk di buka di wireshark, setelah itu pada bagian filter ketik UDP untuk mengfilter.
![tampilan](../assets/image/MOD%205%20(2).png)

## Pertanyaa
1. Field UDP
![tampilan](../assets/image/MOD%205%20Pertanyaan%201.png)

Pada percobaan terdapat 4 field yang tersedia: Source port, Destination port, Lenght, Checksum

2. Panjang masing - masing dari dari field yang ada pada soal 1 yaitu :
- Source port: 2 byte
- Destination port: 2 byte
- Lenght: 2 byte
- Checksum: 2 byte 
di karenakan Header UDP selalu memiliki ukuran tetap 8 byte dan pada percobaan di atas ada 4 field jadi setiap field memiliki panjang 2 byte

3. Lenght 
![tampilan](../assets/image/Pertantaan%203%20MOD%205.png)

Pada gambar yang tertera terlihat bahwa Lenght memiliki panjang 58 yang artinya UDP Payload + Header UDP = 50 + 8 = 58, dan di dapatkan UDP Lenght 58 itu. Jadi, nilai “Length” benar menunjukkan ukuran keseluruhan paket UDP (header + payload).

4. 