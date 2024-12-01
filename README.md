# Jarkom-Modul-5-IT45-2024

| Nama | NRP |
|---|---|
|Dian Anggraeni Putri|5027231016|
|⁠Abhirama Triadyatma Hermawan|5027231061|

# Misi 1: Memetakan Kota New Eridu
## Soal 1
> Sebuah topologi sederhana menggambarkan jaringan New Eridu:
```
Keterangan:
HDD: Berfungsi sebagai DNS Server.
Fairy: Berfungsi sebagai DHCP Server.
Web Servers: HIA, HollowZero.
Client:
  Burnice: Memiliki 5 host.
  Lycaon: Memiliki 20 host.
  Policeboo: Memiliki 30 host.
  Caesar: Memiliki 50 host
  Ellen: Memiliki 100 host.
  Jane: Memiliki 200 host.
```
![image](https://github.com/user-attachments/assets/32ed9f3a-2949-496b-abb2-668b3ffe9a0a)

## Soal 2
> Setelah membagi alamat IP menggunakan VLSM, gambarkan pohon subnet yang menunjukkan hierarki pembagian IP di jaringan New Eridu. Lingkari subnet-subnet yang akan dilewati dalam jaringan
![image](https://github.com/user-attachments/assets/4cff80b5-7c92-4734-9469-dec7145417b0)

### Pembagian IP
| Subnet | Network ID      | Netmask          | Broadcast      | Range IP                |
|--------|-----------------|------------------|----------------|-------------------------|
| A2     | 192.239.0.0     | 255.255.255.0    | 192.239.0.255  | 192.239.0.1 - 192.239.0.254 |
| A4     | 192.239.1.0     | 255.255.255.128  | 192.239.1.127  | 192.239.1.1 - 192.239.1.126 |
| A8     | 192.239.1.128   | 255.255.255.192  | 192.239.1.191  | 192.239.1.129 - 192.239.1.190 |
| A3     | 192.239.1.192   | 255.255.255.248  | 192.239.1.199  | 192.239.1.193 - 192.239.1.198 |
| A6     | 192.239.1.200   | 255.255.255.248  | 192.239.1.207  | 192.239.1.201 - 192.239.1.206 |
| A7     | 192.239.1.208   | 255.255.255.248  | 192.239.1.215  | 192.239.1.209 - 192.239.1.214 |
| A1     | 192.239.1.216   | 255.255.255.252  | 192.239.1.219  | 192.239.1.217 - 192.239.1.218 |
| A5     | 192.239.1.220   | 255.255.255.252  | 192.239.1.223  | 192.239.1.221 - 192.239.1.222 |
| A9     | 192.239.1.224   | 255.255.255.252  | 192.239.1.227  | 192.239.1.225 - 192.239.1.226 |

### Pembagian IP
![image](https://github.com/user-attachments/assets/f99d58f5-2ec5-43ea-b9c8-daf14caecdfe)

## Soal 3
>  Setelah pembagian IP selesai, buatlah konfigurasi rute untuk menghubungkan semua subnet dengan benar di jaringan New Eridu. Pastikan perangkat dapat saling terhubung.

### Subnetting
#### NewEridu
```
#NAT
auto eth0
iface eth0 inet dhcp
#A1
auto eth1
iface eth1 inet static
    address 192.239.1.217
    netmask 255.255.255.252
#A5
auto eth2
iface eth2 inet static
    address 192.239.1.221
    netmask 255.255.255.252
```

#### LuminaSquare
```
#A1
auto eth0
iface eth0 inet static
    address 192.239.1.218
    netmask 255.255.255.252
    gateway 192.239.1.217
#A2
auto eth1
iface eth1 inet static
    address 192.239.0.1
    netmask 255.255.255.0
#A3
auto eth2
iface eth2 inet static
    address 192.239.1.193
    netmask 255.255.255.248
```

Jane
```
auto eth0
iface eth0 inet dhcp
```

Policeboo
```
auto eth0
iface eth0 inet dhcp
```

HIA
```
#A3
auto eth0
iface eth0 inet static
    address 192.239.1.195
    netmask 255.255.255.248
    gateway 192.239.1.193
```

BalletTwins
```
#A3
auto eth0
iface eth0 inet static
    address 192.239.1.194
    netmask 255.255.255.248
    gateway 192.239.1.193
#A4
auto eth1
iface eth1 inet static
    address 192.239.1.1
    netmask 255.255.255.128
```

#### Ellen
```
auto eth0
iface eth0 inet dhcp
```

Lycaon
```
auto eth0
iface eth0 inet dhcp
```

SixStreet
```
#A5
auto eth0
iface eth0 inet static
    address 192.239.1.222
    netmask 255.255.255.252
    gateway 192.239.1.221
#A6
auto eth1
iface eth1 inet static
    address 192.239.1.201
    netmask 255.255.255.248
#A7
auto eth2
iface eth2 inet static
    address 192.239.1.209
    netmask 255.255.255.248
```

Fairy
```
#A6
auto eth0
iface eth0 inet static
    address 192.239.1.202
    netmask 255.255.255.248
    gateway 192.239.1.201
```

HDD
```
#A6
auto eth0
iface eth0 inet static
    address 192.239.1.203
    netmask 255.255.255.248
    gateway 192.239.1.201
```

OuterRing
```
#A7
auto eth0
iface eth0 inet static
    address 192.239.1.210
    netmask 255.255.255.248
    gateway 192.239.1.209
#A8
auto eth1
iface eth1 inet static
    address 192.239.1.129
    netmask 255.255.255.192
```

Caesar
```
auto eth0
iface eth0 inet dhcp
```

Burnice
```
auto eth0
iface eth0 inet dhcp
```

ScootOutpost
```
#A7
auto eth0
iface eth0 inet static
    address 192.239.1.211
    netmask 255.255.255.248
    gateway 192.239.1.209
#A9
auto eth1
iface eth1 inet static
    address 192.239.1.225
    netmask 255.255.255.252
```

HollowZero
```
#A9
auto eth0
iface eth0 inet static
    address 192.239.1.226
    netmask 255.255.255.252
    gateway 192.239.1.225
```

### Routing
#### NewEridu
```
# Rute untuk A1 ke jaringan lain (A2-A4)
post-up route add -net 192.239.0.0 netmask 255.255.255.0 gw 192.239.1.218
post-up route add -net 192.239.1.192 netmask 255.255.255.248 gw 192.239.1.218
post-up route add -net 192.239.1.0 netmask 255.255.255.128 gw 192.239.1.218
# Rute untuk A5 ke jaringan lain (A6-A9)
post-up route add -net 192.239.1.200 netmask 255.255.255.248 gw 192.239.1.222
post-up route add -net 192.239.1.208 netmask 255.255.255.248 gw 192.239.1.222
post-up route add -net 192.239.1.128 netmask 255.255.255.192 gw 192.239.1.222
post-up route add -net 192.239.1.224 netmask 255.255.255.252 gw 192.239.1.222
```

#### LuminaSquare
```
# Rute kembali menuju A1
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.239.1.217
# Rute ke A4
post-up route add -net 192.239.1.0 netmask 255.255.255.128 gw 192.239.1.194
```

#### BalletTwins
```
# Rute kembali ke A1 dan A2
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.239.1.192
```

#### SixStreet
```
# Rute untuk koneksi umum (default route)
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.239.1.221
# Rute menuju A8 dan A9
post-up route add -net 192.239.1.128 netmask 255.255.255.192 gw 192.239.1.210
post-up route add -net 192.239.1.224 netmask 255.255.255.252 gw 192.239.1.211
```

#### OuterRing
```
# Rute umum untuk koneksi kembali
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.239.1.209
# Rute menuju A9
post-up route add -net 192.239.1.224 netmask 255.255.255.252 gw 192.239.1.211
```

#### ScootOutpost
```
# Rute umum kembali ke gateway utama
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.239.1.209
# Rute ke A8
post-up route add -net 192.239.1.128 netmask 255.255.255.192 gw 192.239.1.210
```


