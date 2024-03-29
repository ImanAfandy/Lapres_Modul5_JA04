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

# Interfaces 

# pikachu
<pre>auto eth0
iface eth0 inet static
address 10.151.72.22
netmask 255.255.255.252
gateway 10.151.72.21

auto eth1
iface eth1 inet static
address 192.168.0.5
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.252
</pre> 

# blastoise
<pre>
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.252
gateway 192.168.0.1

auto eth1
iface eth1 inet static
address 192.168.0.129
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 10.151.73.41
netmask 255.255.255.248

#snorlax
auto eth0
iface eth0 inet static
address 192.168.0.130
netmask 255.255.255.128
gateway 192.168.0.129
</pre>

# articuno
<pre>
auto eth0
iface eth0 inet static
address 10.151.73.42
netmask 255.255.255.248
gateway 10.151.73.41
</pre>

# mew
<pre>
auto eth0
iface eth0 inet static
address 10.151.73.43
netmask 255.255.255.248
gateway 10.151.73.41
</pre>

# venesaur
<pre>
auto eth0
iface eth0 inet static
address 192.168.0.6
netmask 255.255.255.252
gateway 192.168.0.5

auto eth1
iface eth1 inet static
address 192.168.0.9
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.1.0
netmask 255.255.255.0
</pre>

# psyduck
<pre>
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.0
</pre>

# arceus
<pre> 
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.252
gateway 192.168.0.9

auto eth1
iface eth1 inet static
address 192.168.0.17
netmask 255.255.255.248
</pre>

# moltres
<pre>
auto eth0
iface eth0 inet static
address 192.168.0.18
netmask 255.255.255.248
gateway 192.168.0.17
</pre>

# mewtwo
<pre>
auto eth0
iface eth0 inet static
address 192.168.0.19
netmask 255.255.255.248
gateway 192.168.0.17
</pre>

# routing
# pikachu 
<pre>
route add -net 192.168.0.128 netmask 255.255.255.128 gw 192.168.0.2 #A1
route add -net 10.151.73.40 netmask 255.255.255.248 gw 192.168.0.2 #DMZ
route add -net 192.168.0.8 netmask 255.255.255.252 gw 192.168.0.6 #A4
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.6 #A5
route add -net 192.168.0.16 netmask 255.255.255.248 gw 192.168.0.6 #A6
</pre>

# blastoise
<pre>
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1
</pre>

# venusaur
<pre>
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.5
route add -net 192.168.0.16 netmask 255.255.255.248 gw 192.168.0.10 #A6
</pre>
# arceus
<pre>
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.9
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.5
</pre>

<p>(1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi
PIKACHU menggunakan iptables, namun Satoshi melarang kalian menggunakan MASQUERADE
karena terlalu mudah.</p>
<p>
 <pre>
 iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o eth0 -j SNAT --to-source 10.151.72.14
 </pre>
Karena keberadaan jaringan tersebut sudah mulai diketahui dari oleh jaringan luar, Satoshi pun
merasa panik, karena merasa jaringannya masih belum aman. (2) Oleh karena itu maka kalian diminta
untuk mendrop semua akses SSH dari luar Topologi (UML) Kalian pada server yang memiliki ip
DMZ (DHCP dan DNS SERVER) pada PIKACHU demi menjaga keamanan.</p>
<pre>
iptables -A INPUT -p tcp --dport 22 -s 10.151.73.24/29 -j DROP
rev: iptables -A FORWARD -p tcp --dport 22 -d 10.151.73.24/29 -i eth0 -j DROP
</pre>

<p>
(3) Karena tim kalian maksimal terdiri dari 2 atau 3 orang saja, Satoshi meminta kalian untuk hanya
membatasi DHCP dan DNS server hanya boleh menerima maksimal 2 atau 3(jumlah kelompok)
koneksi ICMP secara bersamaan yang berasal dari mana saja menggunakan iptables pada masing
masing server, selebihnya akan di DROP.</p>
<pre>
iptables -A OUTPUT -p icmp -m limit --limit 3/second -j ACCEPT
iptables -A INPUT -p icmp -m connlimit -connlimit-above 2 -j DROP
</pre>

<p>
 (4) Kalian juga diminta untuk mengkonfigurasi PIKACHU untuk dapat membedakan ketika MEW
diakses dari subnet AJK, akan diarahkan pada MEWTWO dengan port 1234. </p>
<p>
 <pre>
 iptables -t nat -A PREROUTING -d 10.151.73.27 -s 10.151.36.0/24 -p tcp --dport 1234 -j DNAT --to-destination 192.168.0.19:1234 
 </pre>

 (5) Sedangkan ketika
diakses dari subnet INFORMATIKA akan diarahkan pada MOLTRES dengan port 1234. </p>
 <pre>
 iptables -t nat -A PREROUTING -d 10.151.73.27 -s 10.151.252.0/22 -p tcp --dport 1234 -j DNAT --to-destination 192.168.0.18:1234
 </pre>
 
<p>
kemudian kalian diminta untuk membatasi akses ke MEW yang berasal dari SUBNET AJK dan
SUBNET INFORMATIKA dengan peraturan sebagai berikut,:</p>
<p>
● (6) Akses dari subnet AJK hanya diperbolehkan pada pukul 08.00 - 17.00 pada hari Senin sampai
Jumat, </p>
<pre>
iptables -A INPUT -s 10.151.36.0/24 -m time --timestart 08:00 --timestop 17:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 10.151.36.0/24 -m time --timestart 17:01 --timestop 07:59 -j REJECT
iptables -A INPUT -s 10.151.36.0/24 -m time --timestart 17:00 --timestop 08:00 --weekend Sat,Sun -j REJECT

</pre>
<p>
● (7) Akses dari subnet INFORMATIKA hanya diperbolehkan pada pukul 17.00 hingga pukul
09.00 setiap harinya
Selain itu paket akan di REJECT. </p>
<pre>
iptables -A INPUT -s 10.151.252.0/22 -m time --timestart 08:00 --timestop 17:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
rev: iptables -A INPUT -s 10.151.252.0/22 -m time --timestart 09:01 --timestop 16:59 -j REJEC
</pre>
<p>
Karena kita memiliki 2 buah WEB Server, (9)Satoshi ingin PIKACHU disetting sehingga setiap
request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada
MEWTWO port 80 dan MOLTRES port 80. </p>
<p>
Karena banyak paket yang di drop oleh tim kalian, (10) Satoshi ingin agar semua paket didrop oleh
firewall (dalam topologi) tercatat dalam log pada setiap UML yang memiliki aturan drop. </p>

K
