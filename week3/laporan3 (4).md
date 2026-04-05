# MODUL 4 (DNS)
Domain Name System (DNS) memiliki peran penting dalam infrastruktur internet, ia mentranslasikan nama host ke bentuk alamat IP. Pada modul ini, kita akan mempelajari lebih lanjut sisi klien DNS. Perlu diingat bahwa peran klien dalam DNS relatif sederhana - klien hanya mengirimkan permintaan ke server DNS lokal dan menerima respons balik

## Modul 4.2 Nslookup
nslookup adalah sebuah perintah atau tool yang digunakan untuk mencari dan menampilkan informasi terkait Domain Name System (DNS), seperti mengetahui alamat IP dari sebuah domain atau sebaliknya, sehingga membantu pengguna dalam melakukan pengecekan jaringan dan troubleshooting koneksi.

## Langkah - Langkah percobaan
1. Buka cmd pada device yang di gunakan lalu ketik "nslookup www.mit.edu" lalu ENTER. Berfungsi untuk melihat IP 
![tampilan](../assets/image/Nslookup.png)

2. Buka cmd lalu ketik "nslookup -type=NS mit.edu" lalu ENTER. Fungsinya untuk melihat server yang terhubung di "nslookup -type=NS mit.edu"
![tampilan](../assets/image/nslookup%20(2).png)

3. Buka cmd lalu ketik "nslookup www.aiit.or.kr bitsy.mit.edu" lalu ENTER. Fungsinya menanyakan ke server DNS bitsy.mit.edu tentang IP address dari domain "www.aiit.or.kr."
![tampilan](../assets/image/nslookup%20(3).png)

## Pertanyaan
1. Mencari IP server web di Asia
- Perintah : nslookup www.u-tokyo.ac.jp
- Domain : www.u-tokyo.ac.jp
- Alamat IP : 210.152.243.234
![tampilan](../assets/image/Pertanyaan%20nslookup%201.png)

2. Mencari DNS otoritatif universitas di Eropa
- Perintah : nslookup -type=NS cam.ac.uk
![tampilan](../assets/image/Pertanyaan%20nslookup%202.png)

3. Mencari mail server Yahoo melalui DNS tertentu
- Perintah : nslookup -type=MX gmail.com dns0.cam.ac.uk
![tampilan](../assets/image/Pertanyaan%20nslookup%203.png)
# Modul 4.3 Ipconfig
ipconfig adalah perintah pada sistem operasi Windows yang digunakan untuk menampilkan dan mengelola konfigurasi jaringan pada komputer, seperti alamat IP, subnet mask, dan default gateway, sehingga membantu pengguna mengetahui kondisi dan pengaturan koneksi jaringan yang sedang digunakan.
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

# 4.4 Tracing DNS dengan Wireshark
A. Analisis DNS Request dan Response pada Akses Website (www.ietf.org)

## Langkah - Langkah Percobaan
1. Buka cmd lalu ketik "IPCONFIG" untuk melihat IP lalu copy IP pada laptop masing-masing (192.168.0.100). lalu buka wireshark
![tampilan](../assets/image/tracing%20dns.png)

2. Setelah buka wireshark pilih jaringan yang digunakan (saya menggunakan wifi). Setelah memilih wifi click bagian filter lalu ketik ip.addr == 192.168.0.100 (sesuai hasil di cmd)

3. Buka browser http://www.ietf.org/ 

4. Tambahkan filter lagi ip.addr == 10.218.0.23 && dns.qry.name.contains "ietf"
