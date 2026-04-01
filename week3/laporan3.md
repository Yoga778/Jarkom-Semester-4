# MODUL 4 (DNS)
Domain Name System (DNS) memiliki peran penting dalam infrastruktur internet, ia mentranslasikan nama host ke bentuk alamat IP. Pada modul ini, kita akan mempelajari lebih lanjut sisi klien DNS. Perlu diingat bahwa peran klien dalam DNS relatif sederhana - klien hanya mengirimkan permintaan ke server DNS lokal dan menerima respons balik

## Modul 4.2 Nslookup

## Langkah - Langkah percobaan
1. Buka cmd pada device yang di gunakan lalu ketik "nslookup www.mit.edu" lalu ENTER. Berfungsi untuk melihat IP 
![tampilan](../assets/image/Nslookup.png)

2. Buka cmd lalu ketik "nslookup -type=NS mit.edu" lalu ENTER. Fungsinya untuk melihat server yang terhubung di "nslookup -type=NS mit.edu"
![tampilan](../assets/image/nslookup%20(2).png)

3. Buka cmd lalu ketik "nslookup www.aiit.or.kr bitsy.mit.edu".
![tampilan](../assets/image/nslookup%20(3).png)

# Modul 4.3 Ipconfig

## Langkah - Langkah Percobaan
1. Buka cmd lalu ketik "ipconfig /all" lalu ENTER. fungsi di sini untuk menampilkan ip dan dns pada laptop
![tampilan](../assets/image/ipconfig.png)

2. Buka cmd lalu ketik "ipconfig /all > networkinfo.txt" lalu ENTER. Fungsi sama seperti sebelumnya cuman command tadi di gunakan untuk menyimpan ip dan dns yang sudah di tampilkan. untuk membuka atau melihat hasil (di laptop saya) yaitu buka file explorer lalu masuk ke folder C, setelah itu cari folder User, lalu masuk ke folder asus dan scroll ke bagian bawah.
![tampilan](../assets/image/ipconfig%20(2).png)

![tampilan](../assets/image/ipconfig%20(3).png)


3. Buka cmd lalu ketik "ipconfig /displaydns" lalu ENTER. Fungsinya untuk menampilkan dns
![tampilan](../assets/image/ipconfig%20(4).png)

4. Buka cmd lalu ketik "ipconfig /flushdns" lalu ENTER. Fungsinya untuk menghapus dns yang sudah di buka dalam device yang di gunakan 
![tampilan](../assets/image/ipconfig%20(5).png)

# 4.4 

## Langkah - Langkah Percobaan
1. Buka cmd lalu ketik "IPCONFIG" untuk melihat IP lalu copy IP pada laptop masing-masing. lalu buka wire shark
