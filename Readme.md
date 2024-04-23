# Tugas Praktikum

Buatlah topologi dibawah berikut menggunakan Cisco Packet Tracer dengan mengimplementasikan Routing Static dan Dynamic Routing RIPv2

![App Screenshot](/Image/1.png)

Task:

1. Tampilkan command atau konfigurasi dalam laporan.
2. Berikan penjelasan mengenai hasil `show ip route`,`show running-config` dan saat pengiriman packet data dari sumber ke tujuan pada setiap masing - masing routing protocol (Static maupun RIPv2).

## Tampilkan command atau konfigurasi

Router 1

```bash
Router1(config)# interface gigabitEthernet0/0
Router1(config-if)# ip address 192.168.1.1 255.255.255.0
Router1(config-if)# no shutdown

Router1(config)# interface gigabitEthernet0/1
Router1(config-if)# ip address 10.0.0.1 255.255.255.0
Router1(config-if)# no shutdown

Router1(config)# ip route 10.0.1.0 255.255.255.0 10.0.0.2
```

Router 2

```bash
Router2(config)# interface gigabitEthernet0/0
Router2(config-if)# ip address 192.168.2.1 255.255.255.0
Router2(config-if)# no shutdown

Router2(config)# interface gigabitEthernet0/1
Router2(config-if)# ip address 10.0.0.2 255.255.255.0
Router2(config-if)# no shutdown

Router2(config)# ip route 10.0.2.0 255.255.255.0 10.0.0.1
```

Router 3

```bash
Router3(config)# interface gigabitEthernet0/0
Router3(config-if)# ip address 192.168.3.1 255.255.255.0
Router3(config-if)# no shutdown

Router3(config)# interface gigabitEthernet0/1
Router3(config-if)# ip address 10.0.1.1 255.255.255.0
Router3(config-if)# no shutdown

Router3(config)# ip route 10.0.2.0 255.255.255.0 10.0.1.2
```

Router 4

```bash
Router4(config)# interface gigabitEthernet0/0
Router4(config-if)# ip address 192.168.4.1 255.255.255.0
Router4(config-if)# no shutdown

Router4(config)# interface gigabitEthernet0/1
Router4(config-if)# ip address 10.0.1.2 255.255.255.0
Router4(config-if)# no shutdown

Router4(config)# ip route 10.0.3.0 255.255.255.0 10.0.1.1
```

## Penjelasan Hasil:

1. `show ip route`: Perintah ini menampilkan tabel routing pada router. Untuk routing statis, kita akan melihat entri yang ditambahkan secara manual. Untuk RIPv2, kita akan melihat entri yang diperoleh melalui proses dinamis. Hasilnya:

![App Screenshot](/Image/2.png)

2. `show running-config`: Perintah ini menampilkan konfigurasi berjalan dari router. Anda akan melihat semua konfigurasi yang telah diatur, termasuk konfigurasi antarmuka, routing, dan protokol dinamis seperti RIP. Hasilnya:

![App Screenshot](/Image/3.png)

![App Screenshot](/Image/4.png)

## Saat Pengiriman Packet Data:

Routing Statis:

![App Screenshot](/Image/Rangkaian.png)

![App Screenshot](/Image/6.png)

![App Screenshot](/Image/5.png)

- Saat pengiriman packet data dari sumber ke tujuan menggunakan routing statis, router akan memeriksa tabel routingnya untuk menentukan jalur yang tepat. Packet akan diteruskan ke tujuan sesuai dengan jalur yang ditentukan dalam tabel routing statis.
  Dynamic Routing RIPv2:

- Saat pengiriman packet data dari sumber ke tujuan menggunakan dynamic routing RIPv2, router akan bertukar informasi routing dengan router tetangganya. Packet akan diteruskan ke tujuan berdasarkan informasi dalam tabel routing yang telah diperbarui melalui proses pertukaran informasi.
