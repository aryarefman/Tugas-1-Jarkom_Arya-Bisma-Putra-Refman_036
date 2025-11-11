# TUGAS 1 JARKOM ARYA BISMA PUTRA REFMAN 5027241036

## 1. TOPOLOGI
<img width="1023" height="654" alt="image" src="https://github.com/user-attachments/assets/bdf1cd9f-a6aa-4614-ab5e-5889747c2d20" />

## 2. BASE NETWORK
- NRP: `5027241036`
- `10.<5027241036 mod 256>.0.0` = `10.76.0.0`

## 3. SUBNETTING
#### Berikut adalah hasil perhitungan subnet berdasarkan kebutuhan host di masing-masing bidang.  
| Subnet (Keterangan) | Kebutuhan Host | Block Size | Prefix | Keterangan Tambahan |
|----------------------|----------------|-------------|---------|----------------------|
| Sekretariat | 380 host | 512 | /23 | Menampung seluruh PC staf sekretariat |
| Bidang Kurikulum | 220 host | 256 | /24 | Jaringan untuk komputer bidang kurikulum |
| Bidang Guru & Tendik | 95 host | 128 | /25 | Untuk perangkat guru dan tenaga pendidik |
| Bidang Sarana Prasarana | 45 host | 64 | /26 | Untuk perangkat pengelolaan sarana dan prasarana |
| Bidang Pengawas Sekolah (Cabang) | 18 host | 32 | /27 | Jaringan di kantor cabang |
| Server & Admin | 6 host | 8 | /29 | Menampung server utama dan perangkat admin |
| Link Router (Pusat → Cabang) *(P2P)* | 2 host | 4 | /30 | Koneksi **Point-to-Point** antar-router pusat dan cabang |

#### Total dan Ringkasan
| Keterangan | Nilai |
|-------------|-------|
| **Total Kebutuhan Host** | 766 host |
| **Total Block Size Digunakan** | 1024 alamat (setara dengan 4 × /24) |
| **Prefix Keseluruhan** | `/22` |
| **Network Utama** | `10.76.0.0/22` |
<img width="1047" height="762" alt="image" src="https://github.com/user-attachments/assets/1214dacf-c069-47ce-a8ce-59d53f613f32" />

### - VLSM
| SUBNET (Keterangan) | KEBUTUHAN HOST | BLOCK SIZE | PREFIX | NETMASK | NETWORK ADDRESS | BROADCAST ADDRESS | USABLE IP RANGE | GATEWAY | USABLE HOSTS |
|----------------------|----------------|-------------|---------|----------|------------------|-------------------|----------------|----------|---------------|
| Sekretariat | 380 | 512 | /23 | 255.255.254.0 | 10.76.0.0 | 10.76.1.255 | 10.76.0.1 - 10.76.1.254 | 10.76.0.1 | 510 |
| Bidang Kurikulum | 220 | 256 | /24 | 255.255.255.0 | 10.76.2.0 | 10.76.2.255 | 10.76.2.1 - 10.76.2.254 | 10.76.2.1 | 254 |
| Bidang Guru & Tendik | 95 | 128 | /25 | 255.255.255.128 | 10.76.3.0 | 10.76.3.127 | 10.76.3.1 - 10.76.3.126 | 10.76.3.1 | 126 |
| Bidang Sarana Prasarana | 45 | 64 | /26 | 255.255.255.192 | 10.76.3.128 | 10.76.3.191 | 10.76.3.129 - 10.76.3.190 | 10.76.3.129 | 62 |
| Bidang Pengawas Sekolah (Cabang) | 18 | 32 | /27 | 255.255.255.224 | 10.76.3.192 | 10.76.3.223 | 10.76.3.193 - 10.76.3.222 | 10.76.3.193 | 30 |
| Server & Admin | 6 | 8 | /29 | 255.255.255.248 | 10.76.3.224 | 10.76.3.231 | 10.76.3.225 - 10.76.3.230 | 10.76.3.225 | 6 |
| Link Router (Pusat → Cabang) *(P2P)* | 2 | 4 | /30 | 255.255.255.252 | 10.76.3.232 | 10.76.3.235 | 10.76.3.233 - 10.76.3.234 | — (Router Pusat: .233, Cabang: .234) | 2 |
<img width="646" height="777" alt="image" src="https://github.com/user-attachments/assets/97eef3d3-2bbe-41ce-aa41-8e2f3753bc57" />

### - CIDR
