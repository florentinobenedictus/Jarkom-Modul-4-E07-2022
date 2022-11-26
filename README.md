# Jarkom-Modul-4-E07-2022


| Nama                        | NRP        |
|:---------------------------:|:----------:|
| Arya Nur Razzaq             | 5025201102 |
| Florentino Benedictus       | 5025201222 |
| Muhammad Zufarrifqi Prakoso | 5025201276 |

[Link Miro Kelompok (VLSM & CIDR TREE, Tabel, Sequence CIDR)](https://miro.com/app/board/uXjVPBM25LY=/)

## Soal Modul 4
- [Soal](https://docs.google.com/document/d/1a_ITp6WYIqoJFXA2oL1jkox9AzqYGxicjr2LGPBsqBE/edit)
## VLSM (CPT)
Pertama-tama akan dibuat tabel yang berisi jumlah IP pada tiap subnet dan totalnya<br>
![image](https://user-images.githubusercontent.com/85059763/204088625-bdca2193-01bf-4122-99dc-34162f400271.png)<br>
Selanjutnya, dibuat tree VLSM sebagai berikut<br>
![image](https://user-images.githubusercontent.com/85059763/204088669-d9e612bf-a390-42e8-a61e-1cd7b1207900.png)<br>

### Konfigurasi CPT
Pada CPT, topologi akan dibuat seperti [Modul 4 Jarkom](https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-4), kemudian tiap node (router, host) akan diconfig sesuai dengan IP subnet sehingga IP node maupun gateway akan berada pada range usable IP tiap subnet. Kemudian dilakukan direct routing dan static routing pada tiap router yang berada dalam topologi. Uji coba file .pkt dapat dilakukan dengan mengirimkan pesan dari suatu node ke node lain

![messageImage_1669465101734](https://user-images.githubusercontent.com/103361498/204089414-6405a4bd-87a6-4b9c-a0d9-4763becd3f8f.jpg)


## CIDR (GNS3)

### Topologi
![image](https://user-images.githubusercontent.com/77829361/204077871-9dcb1ff0-5355-43af-ac05-a64402ba8a94.png)
### Penggabungan Subnet
Pengabungan Subnetnya adalah sebagai berikut

![image](https://user-images.githubusercontent.com/77829361/204078551-8e408f17-7458-41d6-b7f5-2762e2ea615e.png)
![image](https://user-images.githubusercontent.com/77829361/204078564-a62f5827-c2a8-4545-8171-8ada6d870d9f.png)
![image](https://user-images.githubusercontent.com/77829361/204078577-8a6d8aa2-c960-486a-927f-ecc7e136cfb8.png)
![image](https://user-images.githubusercontent.com/77829361/204078589-0407710e-9e25-40bc-a416-1893ae0485b0.png)
![image](https://user-images.githubusercontent.com/77829361/204078604-330f21f4-6406-4e0c-b33f-47e9b154b14a.png)
![image](https://user-images.githubusercontent.com/77829361/204078618-14966956-1326-4ca7-8676-e4ee4efa6d08.png)
![image](https://user-images.githubusercontent.com/77829361/204078634-1c8373d8-0634-4b53-ab11-9a9c35b96a9e.png)
![image](https://user-images.githubusercontent.com/77829361/204078664-ed4cdb9d-9a3a-4ee1-a2d1-c4c65bfc443b.png)<br>
Selanjutnya, dari penggabungan subnet dibuat tree CIDR<br>
![image](https://user-images.githubusercontent.com/85059763/204088757-f10c479f-270b-48a8-9be9-f9f73389aeef.png)<br>

### Konfigurasi GNS
#### The Resonance
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.173.64.1
        netmask 255.255.255.252

auto eth2
iface eth2 inet static
         address 192.173.192.1
         netmask 255.255.255.252

auto eth3
iface eth3 inet static
        address 192.173.1.1
        netmask 255.255.255.252

auto eth4
iface eth4 inet static
        address 192.173.32.1
        netmask 255.255.255.252
```
#### The Magical
```
auto eth0
iface eth0 inet static
	address 10.25.100.2
	netmask 255.255.255.252
	gateway 10.25.100.1

auto eth1
iface eth1 inet static
	address 10.25.96.1
	netmask 255.255.254.0
```
#### The Order
```auto eth0
iface eth0 inet static
	address 10.25.32.2
	netmask 255.255.255.252
	gateway 10.25.32.1

auto eth1
iface eth1 inet static
	address 10.25.16.1
	netmask 255.255.255.192

auto eth2
auto eth0
iface eth0 inet static
	address 10.25.32.2
	netmask 255.255.255.252
	gateway 10.25.32.1

auto eth1
iface eth1 inet static
	address 10.25.16.1
	netmask 255.255.255.192

auto eth2
iface eth2 inet static
	address 10.25.8.1
	netmask 255.255.255.252
```
#### The Minister
```
auto eth0
iface eth0 inet static
	address 10.25.8.2
	netmask 255.255.255.252
	gateway 10.25.8.1

auto eth1
iface eth1 inet static
	address 10.25.4.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 10.25.1.1
	netmask 255.255.255.252
```
#### The Dauntless
```
auto eth0
iface eth0 inet static
	address 10.25.1.2
	netmask 255.255.255.252
	gateway 10.25.1.1

auto eth1
iface eth1 inet static
	address 10.25.0.1
	netmask 255.255.255.0
```
#### The Queen
```
auto eth0
iface eth0 inet static
	address 10.25.64.2
	netmask 255.255.255.0
	gateway 10.25.64.1

auto eth1
iface eth1 inet static
	address 10.25.65.1
	netmask 255.255.255.252
```
#### The Instrument
```
auto eth0
iface eth0 inet static
	address 10.25.80.2
	netmask 255.255.255.252
	gateway 10.25.80.1

auto eth1
iface eth1 inet static
	address 10.25.74.1
	netmask 255.255.255.128

auto eth2
iface eth2 inet static
	address 10.25.68.1
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.25.73.1
	netmask 255.255.255.252
```
#### The Profound
```
auto eth0
iface eth0 inet static
	address 10.25.73.2
	netmask 255.255.255.252
	gateway 10.25.73.1

auto eth1
iface eth1 inet static
	address 10.25.72.129
	netmask 255.255.255.128

auto eth2
iface eth2 inet static
	address 10.25.72.1
	netmask 255.255.255.128
```
#### Ashaf
```
auto eth0
iface eth0 inet static
	address 10.25.16.2
	netmask 255.255.255.192
	gateway 10.25.16.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
#### The Beast
```
auto eth0
iface eth0 inet static
	address 10.25.98.2
	netmask 255.255.255.252
	gateway 10.25.98.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Haines
```
auto eth0
iface eth0 inet static
	address 10.25.96.3
	netmask 255.255.254.0
	gateway 10.25.96.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Corvekt
```
auto eth0
iface eth0 inet static
	address 10.25.96.2
	netmask 255.255.254.0
	gateway 10.25.96.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Spendrow
```
auto eth0
iface eth0 inet static
	address 10.25.72.2
	netmask 255.255.255.128
	gateway 10.25.72.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Helga
```
auto eth0
iface eth0 inet static
	address 10.25.72.130
	netmask 255.255.255.128
	gateway 10.25.72.129
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Oakleave
```
auto eth0
iface eth0 inet static
	address 10.25.66.2
	netmask 255.255.254.0
	gateway 10.25.66.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### The Witch
```
auto eth0
iface eth0 inet static
	address 10.25.65.2
	netmask 255.255.255.252
	gateway 10.25.65.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Keith
```
auto eth0
iface eth0 inet static
	address 10.25.64.3
	netmask 255.255.255.0
	gateway 10.25.64.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Johan
```
auto eth0
iface eth0 inet static
	address 10.25.0.2
	netmask 255.255.255.0
	gateway 10.25.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Phanora
```
auto eth0
iface eth0 inet static
	address 10.25.0.3
	netmask 255.255.255.0
	gateway 10.25.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Guideau
```
auto eth0
iface eth0 inet static
	address 10.25.4.2
	netmask 255.255.252.0
	gateway 10.25.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```
#### Setup Static dan Direct Routing
Pada tiap router dilakukan static dan direct routing seperti pada GNS, script pada router dapat dijalankan dengan `bash /root/script.sh`

## Pembagian Tugas
| Nama                        | Nomor      |
|:---------------------------:|:----------:|
| Arya Nur Razzaq             | CPT        |
| Florentino Benedictus       | CIDR & VLSM|
| Muhammad Zufarrifqi Prakoso | GNS3       |
## Kendala
Tidak ada
## Revisi
Tidak ada
