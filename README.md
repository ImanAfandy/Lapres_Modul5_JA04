# Lapres_Modul5_JA04

SOAL SHIFT MODUL 5

<p> 
Satoshi ingin meminta bantuan kepada kalian untuk menjadi tim network engineer dalam usahanya.
Karena kalian telah menguasai ilmu jarkom, dengan senang hati kalian membantu Satoshi untuk
membuat jaringan komputer untuk mereka :) </pre>

<p>
(A) Tugas pertama kalian sebagai tim network engineer adalah membuat topologi jaringan. Satoshi
memberikan rancangan topologi jaringan usahanya sebagai berikut :
</p>

<img src="https://github.com/ImanAfandy/Lapres_Modul5_JA04/blob/master/modul5.png">

<p>
Keterangan : CLOUD diberikan IP TUNTAP

ARTICUNO merupakan DHCP Server diberikan IP DMZ
MEW merupakan DNS Server diberikan IP DMZ
MEWTWO dan MOLTRES merupakan WEB Server
Setiap Server diberikan memory sebesar 128M
Client dan Router diberikan memori sebesar 64M
Jumlah host pada subnet PSYDUCK 150 Host
Jumlah host pada subnet SNORLAX 100 Host
</p>
<p>
(B) karena kalian telah menguasai ilmu Subnetting dan Routing, Satoshi meminta kalian untuk
membuat topologi tersebut menggunakan teknik CIDR atau VLSM. Setelah melakukan subnetting,
</p>
<img src="https://github.com/ImanAfandy/Lapres_Modul5_JA04/blob/master/Pengelompokan%20subneting.png">
<p> disini kami menghitung menggunakan vlsm <p>
 <img src="https://github.com/ImanAfandy/Lapres_Modul5_JA04/blob/master/perhitungan%20vlsm.png">
  
 <p> 
(C) kalian juga diharuskan melakukan routing agar setiap perangkat pada jaringan tersebut dapat
terhubung.
 </p> 
 <p>
(D) Tugas kedua kalian adalah memberikan ip pada subnet SNORLAX dan PSYDUCK secara
dinamis menggunakan bantuan DHCP SERVER. Kemudian kalian mengingat bahwa kalian harus
setting DHCP RELAY pada router yang menghubungkannya, seperti yang kalian telah pelajari di
modul 3.</p>
<p>(1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi
PIKACHU menggunakan iptables, namun Satoshi melarang kalian menggunakan MASQUERADE
karena terlalu mudah.</p>
<p>
Karena keberadaan jaringan tersebut sudah mulai diketahui dari oleh jaringan luar, Satoshi pun
merasa panik, karena merasa jaringannya masih belum aman. (2) Oleh karena itu maka kalian diminta
untuk mendrop semua akses SSH dari luar Topologi (UML) Kalian pada server yang memiliki ip
DMZ (DHCP dan DNS SERVER) pada PIKACHU demi menjaga keamanan.</p>
<p>
(3) Karena tim kalian maksimal terdiri dari 2 atau 3 orang saja, Satoshi meminta kalian untuk hanya
membatasi DHCP dan DNS server hanya boleh menerima maksimal 2 atau 3(jumlah kelompok)
koneksi ICMP secara bersamaan yang berasal dari mana saja menggunakan iptables pada masing
masing server, selebihnya akan di DROP.</p>

<p>(4) Kalian juga diminta untuk mengkonfigurasi PIKACHU untuk dapat membedakan ketika MEW
diakses dari subnet AJK, akan diarahkan pada MEWTWO dengan port 1234. </p>
<p>(5) Sedangkan ketika
diakses dari subnet INFORMATIKA akan diarahkan pada MOLTRES dengan port 1234. </p>
<p>
kemudian kalian diminta untuk membatasi akses ke MEW yang berasal dari SUBNET AJK dan
SUBNET INFORMATIKA dengan peraturan sebagai berikut,:
● (6) Akses dari subnet AJK hanya diperbolehkan pada pukul 08.00 - 17.00 pada hari Senin sampai
Jumat, </p>
<p>
● (7) Akses dari subnet INFORMATIKA hanya diperbolehkan pada pukul 17.00 hingga pukul
09.00 setiap harinya
Selain itu paket akan di REJECT. </p>
<p>
Karena kita memiliki 2 buah WEB Server, (9)Satoshi ingin PIKACHU disetting sehingga setiap
request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada
MEWTWO port 80 dan MOLTRES port 80. </p>
<p>
Karena banyak paket yang di drop oleh tim kalian, (10) Satoshi ingin agar semua paket didrop oleh
firewall (dalam topologi) tercatat dalam log pada setiap UML yang memiliki aturan drop. </p>

K
