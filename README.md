# Konfigurasi-VLAN-Cisco-Packet-Tracer

Repository ini berisi tugas individu mata kuliah Jaringan Komputer Terapan 1 tentang konfigurasi Virtual LAN (VLAN) pada jaringan komputer.

## Deskripsi

Tugas ini bertujuan untuk mengimplementasikan VLAN pada jaringan komputer menggunakan Cisco Packet Tracer. Pada tugas ini, dilakukan penambahan satu switch baru (SW-4) serta dua VLAN baru (VLAN 50 dan VLAN 60) yang hanya terdapat pada dua switch tertentu.

## Topologi Jaringan

```
    +--------+      +--------+
    |        |      |        |
    |  SW-1  |------|  SW-2  |
    |        |      |        |
    +--------+      +--------+
        |               |
        |               |
    +--------+      +--------+
    |        |      |        |
    |  SW-3  |------|  SW-4  |
    |        |      |        |
    +--------+      +--------+
```

## Konfigurasi VLAN

### SW-1

| VLAN ID | Nama VLAN | Port Range |
|---------|-----------|------------|
| 10      | Marketing | fa0/3-7    |
| 20      | Sales     | fa0/8-13   |
| 30      | HRD       | fa0/14-18  |
| 40      | Finance   | fa0/19-24  |
| 50      | Research  | -          |
| 60      | Development | -        |

### SW-2

| VLAN ID | Nama VLAN | Port Range |
|---------|-----------|------------|
| 30      | Humas     | -          |
| 40      | Media     | fa0/11-20  |

### SW-3

| VLAN ID | Nama VLAN | Port Range |
|---------|-----------|------------|
| 10      | Marketing | -          |
| 20      | Sales     | fa0/11-20  |

### SW-4

| VLAN ID | Nama VLAN | Port Range |
|---------|-----------|------------|
| 50      | Research  | fa0/3-7    |
| 60      | Development | fa0/8-13  |

## Hasil Konfigurasi

### SW-1

```
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2
10   Marketing                        active    Fa0/3, Fa0/4, Fa0/5, Fa0/6, Fa0/7
20   Sales                            active    Fa0/8, Fa0/9, Fa0/10, Fa0/11, Fa0/12, Fa0/13
30   HRD                              active    Fa0/14, Fa0/15, Fa0/16, Fa0/17, Fa0/18
40   Finance                          active    Fa0/19, Fa0/20, Fa0/21, Fa0/22, Fa0/23, Fa0/24
50   Research                         active    
60   Development                      active    
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
```

### SW-2

```
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24
30   Humas                            active    
40   Media                            active    Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/19, Fa0/20
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
```

### SW-3

```
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24
10   Marketing                        active    
20   Sales                            active    Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/19, Fa0/20
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
```

### SW-4

```
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/14, Fa0/15
                                                Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                Fa0/24
50   Research                         active    Fa0/3, Fa0/4, Fa0/5, Fa0/6, Fa0/7
60   Development                      active    Fa0/8, Fa0/9, Fa0/10, Fa0/11, Fa0/12, Fa0/13
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
```

## Hasil Testing

### Testing Antar VLAN yang Sama

| Dari VLAN | Ke VLAN | Hasil |
|-----------|---------|-------|
| 10 (SW-1) | 10 (SW-3) | Success |
| 20 (SW-1) | 20 (SW-3) | Success |
| 30 (SW-1) | 30 (SW-2) | Success |
| 40 (SW-1) | 40 (SW-2) | Success |
| 50 (SW-1) | 50 (SW-4) | Success |
| 60 (SW-1) | 60 (SW-4) | Success |

### Testing Antar VLAN yang Berbeda

| Dari VLAN | Ke VLAN | Hasil |
|-----------|---------|-------|
| 10 (SW-1) | 20 (SW-1) | Failed |
| 30 (SW-2) | 40 (SW-2) | Failed |
| 50 (SW-4) | 60 (SW-4) | Failed |
| 10 (SW-1) | 50 (SW-4) | Failed |

## Kesimpulan

Dari hasil pengujian, dapat disimpulkan bahwa:
1. Konfigurasi VLAN telah berhasil diimplementasikan pada semua switch.
2. Perangkat dalam satu VLAN yang sama dapat saling berkomunikasi meskipun berada pada switch yang berbeda.
3. Perangkat dalam VLAN yang berbeda tidak dapat saling berkomunikasi sesuai dengan konsep VLAN.
4. Penambahan SW-4 serta VLAN 50 dan VLAN 60 telah berhasil dilakukan dan berfungsi dengan baik.

---
**luqmanaru**
