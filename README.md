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
|                Server & Admin                | 7 host                                | 16               | /28        | Menampung server utama dan perangkat admin                     |
| **Interlink Kantor Pusat (Router -> Switch)** | 6 host                                | 8               | /29        | Menghubungkan router pusat dengan switch utama di kantor pusat |
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
<img width="1162" height="1295" alt="image" src="https://github.com/user-attachments/assets/a2568fb5-f515-423b-bf25-b1807cda5fd3" />

| **Subnet (Keterangan)**                  | **Kebutuhan Host (termasuk gateway)** | **Block Size** | **Prefix** |         **Netmask** | **Network Address** | **Broadcast Address** | **Usable IP Range**         | **Gateway**                          | **Usable Hosts** |
| ---------------------------------------- | ------------------------------------: | -------------: | ---------: | ------------------: | ------------------: | --------------------: | --------------------------- | ------------------------------------ | ---------------: |
| Sekretariat                              |                                   381 |            512 |        /23 |       255.255.254.0 |           10.76.2.0 |           10.76.3.255 | 10.76.2.1 – 10.76.3.254     | 10.76.2.1                            |              510 |
| Bidang Kurikulum                         |                                   221 |            256 |        /24 |       255.255.255.0 |           10.76.1.0 |           10.76.1.255 | 10.76.1.1 – 10.76.1.254     | 10.76.1.1                            |              254 |
| Bidang Guru & Tendik                     |                                    96 |            128 |        /25 |     255.255.255.128 |         10.76.0.128 |           10.76.0.255 | 10.76.0.129 – 10.76.0.254   | 10.76.0.129                          |              126 |
| Bidang Sarana Prasarana                  |                                    46 |             64 |        /26 |     255.255.255.192 |          10.76.0.64 |           10.76.0.127 | 10.76.0.65 – 10.76.0.126    | 10.76.0.65                           |               62 |
| Bidang Pengawas Sekolah (Cabang)         |                                    19 |             32 |        /27 |     255.255.255.224 |          10.76.0.32 |            10.76.0.63 | 10.76.0.33 – 10.76.0.62     | 10.76.0.33                           |               30 |
| Server & Admin          |                                     7 |         16|    /28 | 255.255.255.240 |      10.76.0.16 |        10.76.0.31 | 10.76.0.17 – 10.76.0.30 | 10.76.0.17                       |           14 |
| Interlink Kantor Pusat (Router → Switch) |                                     6 |              8 |        /29 |     255.255.255.248 |           10.76.0.8 |            10.76.0.15 | 10.76.0.9 – 10.76.0.14      | 10.76.0.9                            |                6 |
| Link Router (Pusat → Cabang) *(P2P)*     |                                     2 |              4 |        /30 |     255.255.255.252 |           10.76.0.0 |             10.76.0.3 | 10.76.0.1 – 10.76.0.2       | Pusat: 10.76.0.1 / Cabang: 10.76.0.2 |                2 |

### - CIDR
<img width="949" height="721" alt="image" src="https://github.com/user-attachments/assets/457cb4bd-029d-4a7c-b76c-50170004a8cf" />
<img width="705" height="345" alt="image" src="https://github.com/user-attachments/assets/eb258069-9aa3-44d0-b6bb-b8688cb1cf1e" />

| **Subnet** | **Nama Subnet**                  | **Network / Prefix** |   **Netmask**   | **Network Address** | **Broadcast** |  **Range Host (usable)**  | **Gateway (first usable)** |
| ---------: | :------------------------------- | :------------------: | :-------------: | :-----------------: | :-----------: | :-----------------------: | :------------------------: |
|         A1 | Sekretariat                      |     10.76.0.0/23     |  255.255.254.0  |      10.76.0.0      |  10.76.1.255  |  10.76.0.1 – 10.76.1.254  |          10.76.0.1         |
|         A2 | Bidang Kurikulum                 |     10.76.2.0/24     |  255.255.255.0  |      10.76.2.0      |  10.76.2.255  |  10.76.2.1 – 10.76.2.254  |          10.76.2.1         |
|         A3 | Bidang Guru & Tendik             |     10.76.3.0/25     | 255.255.255.128 |      10.76.3.0      |  10.76.3.127  |  10.76.3.1 – 10.76.3.126  |          10.76.3.1         |
|         A4 | Bidang Sarana Prasarana          |    10.76.3.128/26    | 255.255.255.192 |     10.76.3.128     |  10.76.3.191  | 10.76.3.129 – 10.76.3.190 |         10.76.3.129        |
|         A6 | Server & Admin                   |    10.76.3.192/28    | 255.255.255.240 |     10.76.3.192     |  10.76.3.207  | 10.76.3.193 – 10.76.3.206 |         10.76.3.193        |
|         A7 | Router (Interlink)               |    10.76.3.208/29    | 255.255.255.248 |     10.76.3.208     |  10.76.3.215  | 10.76.3.209 – 10.76.3.214 |         10.76.3.209        |
|         A5 | Bidang Pengawas Sekolah (Cabang) |     10.76.4.0/27     | 255.255.255.224 |      10.76.4.0      |   10.76.4.31  |   10.76.4.1 – 10.76.4.30  |          10.76.4.1         |
|         A8 | Tunnel / Point-to-Point (P2P)    |     10.76.4.32/30    | 255.255.255.252 |      10.76.4.32     |   10.76.4.35  |  10.76.4.33 – 10.76.4.34  |         10.76.4.33         |


|    **LEVEL**   | **Keterangan Penggabungan**                                                                                                                               | **Subnet / Hasil Gabungan** | **Prefix** |    **Netmask**    | **Network Address** | **Broadcast Address** |   **Range Host (usable)**   | **Gateway (first usable)** |
| :------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------: | :--------: | :---------------: | :-----------------: | :-------------------: | :-------------------------: | :------------------------: |
|     Level 1    | Gabungkan semua subnet di `10.76.3.x` (A3,A4,A6,A7)                                                                                                       |       **10.76.3.0/24**      |     /24    |   255.255.255.0   |      10.76.3.0      |      10.76.3.255      |   10.76.3.1 – 10.76.3.254   |          10.76.3.1         |
|     Level 2    | Gabungkan 10.76.2.0/24 (A2) + 10.76.3.0/24                                                                                                                |       **10.76.2.0/23**      |     /23    |   255.255.254.0   |      10.76.2.0      |      10.76.3.255      |   10.76.2.1 – 10.76.3.254   |          10.76.2.1         |
|     Level 3    | Gabungkan 10.76.0.0/23 (A1) + 10.76.2.0/23 (Level2) → membentuk blok lebih besar                                                                          |       **10.76.0.0/22**      |     /22    |   255.255.252.0   |      10.76.0.0      |      10.76.3.255      |   10.76.0.1 – 10.76.3.254   |          10.76.0.1         |
| Level 4 (Root) | **Gabungkan seluruh blok 10.76.0.0/22 (Level3)** dengan blok **10.76.4.0/26** (dan area 4.x di tree) — supaya menutup semua subnet di tree → root minimal |       **10.76.0.0/21**      |   **/21**  | **255.255.248.0** |    **10.76.0.0**    |    **10.76.7.255**    | **10.76.0.1 – 10.76.7.254** |        **10.76.0.1**       |
