# Tugas Praktikum

Buatlah topologi dibawah berikut menggunakan Cisco Packet Tracer dengan mengimplementasikan Routing Static dan Dynamic Routing RIPv2

![App Screenshot](/Image/1.png)

Task:

1. Tampilkan command atau konfigurasi dalam laporan.
2. Berikan penjelasan mengenai hasil `show ip route`,`show running-config` dan saat pengiriman packet data dari sumber ke tujuan pada setiap masing - masing routing protocol (Static maupun RIPv2).

## Tampilkan command atau konfigurasi

Router 1

```bash
Router1(config)# interface FastEthernet0/0
Router1(config-if)# ip address 192.168.2.1 255.255.255.0
Router1(config-if)# no shutdown

Router1(config)# interface Serial0/0/0
Router1(config-if)# ip address 10.0.0.1 255.255.255.0
Router1(config-if)# no shutdown
```

```bash
Router1(config)# ip route 192.168.20.0 255.255.255.0 10.10.10.2
Router1(config)# ip route 10.20.10.0 255.255.255.0 10.10.10.2
Router1(config)# ip route 192.168.40.0 255.255.255.0 10.10.10.2
Router1(config)# ip route 10.30.10.0 255.255.255.0 10.10.10.2
Router1(config)# ip route 172.16.10.0 255.255.255.0 10.10.10.2
```

```bash
Router1(config)# router rip
Router1(config-router)# version 2
Router1(config-router)# network 192.168.2.0
Router1(config-router)# network 10.0.0.0
Router1(config-router)# network 192.168.20.0
Router1(config-router)# network 192.168.40.0
Router1(config-router)# network 172.16.0.0
```

Router 2

```bash
Router2(config)# interface FastEthernet0/0
Router2(config-if)# ip address 192.168.20.1 255.255.255.0
Router2(config-if)# no shutdown

Router2(config)# interface Serial0/0/0
Router2(config-if)# ip address 10.0.0.2 255.255.255.0
Router2(config-if)# no shutdown

Router2(config)# interface Serial0/0/1
Router2(config-if)# ip address 10.20.10.1 255.255.255.0
Router2(config-if)# no shutdown
```

```bash
Router2(config)# ip route 192.168.2.0 255.255.255.0 10.10.10.1
Router2(config)# ip route 192.168.40.0 255.255.255.0 10.20.10.2
Router2(config)# ip route 10.30.10.0 255.255.255.0 10.20.10.2
Router2(config)# ip route 172.16.10.0 255.255.255.0 10.20.10.2
```

```bash
Router2(config)# router rip
Router2(config-router)# version 2
Router2(config-router)# network 192.168.20.0
Router2(config-router)# network 10.0.0.0
Router2(config-router)# network 192.168.2.0
Router2(config-router)# network 192.168.40.0
Router2(config-router)# network 172.16.0.0
```

Router 3

```bash
Router3(config)# interface FastEthernet0/0
Router3(config-if)# ip address 192.168.40.1 255.255.255.0
Router3(config-if)# no shutdown

Router3(config)# interface Serial0/0/0
Router3(config-if)# ip address 10.20.10.2 255.255.255.0
Router3(config-if)# no shutdown

Router3(config)# interface Serial0/0/1
Router3(config-if)# ip address 10.30.10.1 255.255.255.0
Router3(config-if)# no shutdown
```

```bash
Router3(config)# ip route 172.16.20.0 255.255.255.0 10.30.10.2
Router3(config)# ip route 192.168.20.0 255.255.255.0 10.20.10.1
Router3(config)# ip route 10.10.10.0 255.255.255.0 10.20.10.1
Router3(config)# ip route 192.168.2.0 255.255.255.0 10.20.10.1
```

```bash
Router3(config)# router rip
Router3(config-router)# version 2
Router3(config-router)# network 192.168.40.0
Router3(config-router)# network 10.0.0.0
Router3(config-router)# network 172.16.0.0
Router3(config-router)# network 192.168.20.0
Router3(config-router)# network 192.168.2.0
```

Router 4

```bash
Router4(config)# interface FastEthernet0/0
Router4(config-if)# ip address 172.16.10.1 255.255.255.0
Router4(config-if)# no shutdown

Router4(config)# interface Serial0/0/0
Router4(config-if)# ip address 10.30.10.2 255.255.255.0
Router4(config-if)# no shutdown
```

```bash
Router4(config)# ip route 192.168.40.0 255.255.255.0 10.30.10.1
Router4(config)# ip route 10.20.10.0 255.255.255.0 10.30.10.1
Router4(config)# ip route 192.168.20.0 255.255.255.0 10.30.10.1
Router4(config)# ip route 10.10.10.0 255.255.255.0 10.30.10.1
Router4(config)# ip route 192.168.2.0 255.255.255.0 10.30.10.1
```

```bash
Router4(config)# router rip
Router4(config-router)# version 2
Router4(config-router)# network 172.16.0.0
Router4(config-router)# network 10.0.0.0
Router4(config-router)# network 192.168.40.0
Router4(config-router)# network 192.168.20.0
Router4(config-router)# network 192.168.2.0
```

## Penjelasan Hasil:

1. `show ip route`: Perintah ini menampilkan tabel routing pada router. Untuk routing statis, kita akan melihat entri yang ditambahkan secara manual. Untuk RIPv2, kita akan melihat entri yang diperoleh melalui proses dinamis. Hasilnya:

![App Screenshot](/Image/2.png)

2. `show running-config`: Perintah ini menampilkan konfigurasi berjalan dari router. Anda akan melihat semua konfigurasi yang telah diatur, termasuk konfigurasi antarmuka, routing, dan protokol dinamis seperti RIP. Hasilnya:

![App Screenshot](/Image/3.png)

![App Screenshot](/Image/4.png)

## Saat Pengiriman Packet Data:

![App Screenshot](/Image/Rangkaian.png)

![App Screenshot](/Image/6.png)

![App Screenshot](/Image/5.png)

Routing Statis:

- Saat pengiriman packet data dari sumber ke tujuan menggunakan routing statis, router akan memeriksa tabel routingnya untuk menentukan jalur yang tepat. Packet akan diteruskan ke tujuan sesuai dengan jalur yang ditentukan dalam tabel routing statis.
  Dynamic Routing RIPv2:

- Saat pengiriman packet data dari sumber ke tujuan menggunakan dynamic routing RIPv2, router akan bertukar informasi routing dengan router tetangganya. Packet akan diteruskan ke tujuan berdasarkan informasi dalam tabel routing yang telah diperbarui melalui proses pertukaran informasi.
