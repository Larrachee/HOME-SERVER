# 🖥️ Custom-Built Home Server: NAS, Web Hosting, & Minecraft Server

Proyek ini berisi panduan konfigurasi, dokumentasi, dan seluruh berkas pengelolaan untuk membangun server mandiri (*Home Server*) multifungsi berskala lokal yang berjalan 24/7. Server ini memanfaatkan teknologi kontainerisasi dan virtualisasi untuk memisahkan kebutuhan penyimpanan data terpusat (NAS), web hosting aplikasi pribadi, serta server permainan (*dedicated game server*) yang responsif.

---

## 🚀 Fitur & Fungsi Utama Server

### 1. Network Attached Storage (NAS)
* **Penyimpanan Terpusat**: Mengamankan data, foto, video, dan dokumen penting dari berbagai perangkat di satu tempat.
* **Berbagi Berkas (File Sharing)**: Menggunakan protokol SMB/NFS untuk transfer file cepat di jaringan lokal (Windows, macOS, Linux, Android/iOS).
* **Pencadangan Otomatis**: Sistem backup terjadwal untuk meminimalisir risiko kehilangan data penting.

### 2. Web Hosting Platform
* **Aplikasi Berbasis Web**: Siap digunakan untuk meng-hosting website portofolio, landing page, atau aplikasi web pribadi.
* **Reverse Proxy & SSL**: Konfigurasi otomatis untuk mengarahkan domain lokal/publik secara aman menggunakan HTTPS.
* **Containerized Environment**: Menggunakan Docker untuk isolasi aplikasi yang ringan, efisien, dan mudah dirawat.

### 3. Minecraft Game Server
* **Dedicated Server**: Menjalankan server Minecraft mandiri yang selalu aktif tanpa bergantung pada layanan pihak ketiga.
* **Custom Mods & Plugins**: Mendukung optimasi performa (Paper/Purpur) serta pemasangan modifikasi sesuai kebutuhan pemain.
* **Manajemen Otomatis**: Sistem pencadangan dunia (*world backup*) otomatis dan restart terjadwal untuk menjaga kestabilan TPS (*ticks per second*).

---

## 🛠️ Spesifikasi & Kebutuhan Sistem

### 1. Perangkat Keras (Hardware)
* **CPU**: AMD Ryzen 5 5500GT (6 Cores, 12 Threads, up to 4.4GHz)
* **RAM**: 32GB (1x32GB Single Channel) TeamGroup DDR4
* **Penyimpanan**: 512GB NVMe SSD (Digunakan bersama untuk OS, Web Apps, dan Game Server Data)
* **Kabel Jaringan**: LAN Cat 6

### 2. Topologi Jaringan & Keterbatasan Bandwidth (Network Topology)
Untuk mengatasi keterbatasan port pada modem utama bawaan ISP, jaringan rumah dan server dikonfigurasi dengan skema *switch/bridge* lokal menggunakan router tambahan (Tenda AC6) melalui koneksi kabel murni:

```text
[ ISP / Modem Utama ] 
          │
          └──► (Kabel LAN) ──► [ Port LAN - Router Tenda AC6 ] 
                                          │
                         ┌────────────────┴────────────────┐
                         │                                 │
                   (Kabel LAN Cat 6)                 (Kabel LAN)
                         │                                 │
                         ▼                                 ▼
                  [ PC Home Server ]                   [ Laptop ]
```
📁 Struktur Direktori Proyek (Rekomendasi)
```text
.
├── docker/
│   ├── nginx-proxy-manager/   # Konfigurasi Reverse Proxy
│   └── web-apps/              # Berkas source code / kontainer web hosting
├── minecraft/
│   └── server/                # Data core server, plugins, dan dunia Minecraft
└── nas-config/                # Skrip mounting & konfigurasi share folder (SMB/NFS)
```
📝 Catatan Tambahan Pemeliharaan
- Manajemen RAM: Dengan kapasitas RAM 32GB satu keping, server memiliki ruang upgrade yang luas ke depan jika ingin menambah kapasitas menjadi Dual Channel. Alokasikan kapasitas RAM secara bijak antar kontainer Docker dan VM server Minecraft agar host tetap stabil.
- Suhu & Backup: Pastikan sirkulasi udara pada PC Home Server terjaga dengan baik mengingat server beroperasi secara terus-menerus (24/7).
