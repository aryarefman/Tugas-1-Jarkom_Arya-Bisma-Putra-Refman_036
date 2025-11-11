# TUGAS 1 JARKOM ARYA BISMA PUTRA REFMAN 5027241036

## 1. TOPOLOGI
<img width="1023" height="654" alt="image" src="https://github.com/user-attachments/assets/bdf1cd9f-a6aa-4614-ab5e-5889747c2d20" />

## 2. BASE NETWORK
- NRP: `5027241036`
- `10.<5027241036 mod 256>.0.0` = `10.76.0.0`

## 3. SUBNETTING
#### Berikut adalah hasil perhitungan subnet berdasarkan kebutuhan host di masing-masing bidang.  
|            **Subnet (Keterangan)**           | **Kebutuhan Host (termasuk gateway)** | **Block Size**  | **Prefix** | **Keterangan Tambahan**                                        |
| :------------------------------------------: | :------------------------------------ | :-------------- | :--------- | :------------------------------------------------------------- |
|                  Sekretariat                 | 381 host                              | 512             | /23        | Menampung seluruh PC staf sekretariat                          |
|               Bidang Kurikulum               | 221 host                              | 256             | /24        | Jaringan untuk komputer bidang kurikulum                       |
|             Bidang Guru & Tendik             | 96 host                               | 128             | /25        | Untuk perangkat guru dan tenaga pendidik                       |
|            Bidang Sarana Prasarana           | 46 host                               | 64              | /26        | Untuk perangkat pengelolaan sarana dan prasarana               |
|       Bidang Pengawas Sekolah (Cabang)       | 19 host                               | 32              | /27        | Jaringan di kantor cabang                                      |
|                Server & Admin                | 7 host                                | 8               | /29        | Menampung server utama dan perangkat admin                     |
| **Interlink Kantor Pusat (Router -> Switch)** | 7 host                                | 8               | /29        | Menghubungkan router pusat dengan switch utama di kantor pusat |
|   **Link Router (Pusat → Cabang) *(P2P)***   | 2 host                                | 4               | /30        | Koneksi **Point-to-Point** antar-router pusat dan cabang       |
|                   **TOTAL**                  | **778 host**                          | **1024 alamat** | **/22**    | **Semua subnet tercakup dalam jaringan utama 10.76.0.0/22**    |

#### Total dan Ringkasan
| Keterangan | Nilai |
|-------------|-------|
| **Total Kebutuhan Host** | 778 host |
| **Total Block Size Digunakan** | 1024 alamat (setara dengan 4 × /24) |
| **Prefix Keseluruhan** | `/22` |
| **Network Utama** | `10.76.0.0/22` |
<img width="1092" height="760" alt="image" src="https://github.com/user-attachments/assets/9a3363c6-497b-4b80-82e8-a01b85ba8d7a" />

### - VLSM
| **Subnet (Keterangan)**                  | **Kebutuhan Host** | **Block Size** | **Prefix** | **Netmask**     | **Network Address** | **Broadcast Address** | **Usable IP Range**       | **Gateway**                              | **Usable Hosts** |
| ---------------------------------------- | ------------------ | -------------- | ---------- | --------------- | ------------------- | --------------------- | ------------------------- | ---------------------------------------- | ---------------- |
| Sekretariat                              | 380                | 512            | /23        | 255.255.254.0   | 10.76.0.0           | 10.76.1.255           | 10.76.0.1 – 10.76.1.254   | 10.76.0.1                                | 510              |
| Bidang Kurikulum                         | 220                | 256            | /24        | 255.255.255.0   | 10.76.2.0           | 10.76.2.255           | 10.76.2.1 – 10.76.2.254   | 10.76.2.1                                | 254              |
| Bidang Guru & Tendik                     | 95                 | 128            | /25        | 255.255.255.128 | 10.76.3.0           | 10.76.3.127           | 10.76.3.1 – 10.76.3.126   | 10.76.3.1                                | 126              |
| Bidang Sarana Prasarana                  | 45                 | 64             | /26        | 255.255.255.192 | 10.76.3.128         | 10.76.3.191           | 10.76.3.129 – 10.76.3.190 | 10.76.3.129                              | 62               |
| Bidang Pengawas Sekolah (Cabang)         | 18                 | 32             | /27        | 255.255.255.224 | 10.76.3.192         | 10.76.3.223           | 10.76.3.193 – 10.76.3.222 | 10.76.3.193                              | 30               |
| Server & Admin                           | 6                  | 8              | /29        | 255.255.255.248 | 10.76.3.224         | 10.76.3.231           | 10.76.3.225 – 10.76.3.230 | 10.76.3.225                              | 6                |
| Interlink Kantor Pusat (Router → Switch) | 6                  | 8              | /29        | 255.255.255.248 | 10.76.3.232         | 10.76.3.239           | 10.76.3.233 – 10.76.3.238 | 10.76.3.233                              | 6                |
| Link Router (Pusat → Cabang) *(P2P)*     | 2                  | 4              | /30        | 255.255.255.252 | 10.76.3.240         | 10.76.3.243           | 10.76.3.241 – 10.76.3.242 | Pusat: 10.76.3.241 / Cabang: 10.76.3.242 | 2                |
<img width="1014" height="1257" alt="image" src="https://github.com/user-attachments/assets/93806704-380f-4586-b1f6-4a896438c680" />

### - CIDR
|  **LEVEL**  | **KETERANGAN PENGGABUNGAN**                                    | **SUBNET / HASIL GABUNGAN** |       **PREFIX**       |   **NETMASK**   |   **NETWORK ADDRESS**   | **BROADCAST ADDRESS** |            **RANGE IP**           | **CATATAN**                                          |
| :---------: | :------------------------------------------------------------- | :-------------------------- | :--------------------: | :-------------: | :---------------------: | :-------------------: | :-------------------------------: | :--------------------------------------------------- |
| **Level 0** | Subnet awal hasil VLSM (A–H)                                   | A–H (lihat tabel subnet)    | Bervariasi (/23 – /30) |        —        | 10.76.0.0 – 10.76.3.243 |           —           | Tiap subnet punya rentang sendiri | Titik awal sebelum CIDR                              |
| **Level 1** | Gabungkan blok berdekatan di 10.76.3.x → **D + E + F + G + H** | **10.76.3.128/25**          |           /25          | 255.255.255.128 |       10.76.3.128       |      10.76.3.255      |     10.76.3.128 – 10.76.3.255     | Semua subnet kecil (D–H) digabung jadi satu blok /25 |
| **Level 2** | Gabungkan seluruh 10.76.3.x → **C + D1**                       | **10.76.3.0/24**            |           /24          |  255.255.255.0  |        10.76.3.0        |      10.76.3.255      |      10.76.3.0 – 10.76.3.255      | Dua blok /25 berurutan digabung menjadi /24          |
| **Level 3** | Gabungkan 10.76.2.x dan 10.76.3.x → **B + C1**                 | **10.76.2.0/23**            |           /23          |  255.255.254.0  |        10.76.2.0        |      10.76.3.255      |      10.76.2.0 – 10.76.3.255      | Dua blok /24 berurutan digabung menjadi /23          |
| **Level 4** | Gabungkan A (10.76.0.0/23) dan B1 (10.76.2.0/23)               | **10.76.0.0/22**            |           /22          |  255.255.252.0  |        10.76.0.0        |      10.76.3.255      |      10.76.0.0 – 10.76.3.255      | Dua blok /23 membentuk blok besar /22                |
| **Level 5** | Root final menutup semua subnet A–H                            | **10.76.0.0/22**            |           /22          |  255.255.252.0  |        10.76.0.0        |      10.76.3.255      |      10.76.0.0 – 10.76.3.255      | /22 mencakup semua subnet A–H, tidak perlu /21       |

#### Ringkasan Parameter CIDR
| **PARAMETER**                    | **NILAI**                                                     |
| :------------------------------- | :------------------------------------------------------------ |
| **Network Address (ROOT Final)** | `10.76.0.0/22`                                                |
| **Netmask**                      | `255.255.252.0`                                               |
| **Wildcard Mask**                | `0.0.3.255`                                                   |
| **Broadcast Address**            | `10.76.3.255`                                                 |
| **Range IP (full)**              | `10.76.0.0 – 10.76.3.255`                                     |
| **Total IP Address**             | `1024`                                                        |
| **Usable IP Address**            | `1022`                                                        |
| **First Usable IP**              | `10.76.0.1`                                                   |
| **Last Usable IP**               | `10.76.3.254`                                                 |
| **Catatan**                      | /22 mencakup seluruh subnet (A–H), termasuk Interlink dan P2P |
