Materi Minggu 1: Paradigma Cloud Computing dan Gerakan Open Source
Prompt: "Buatkan rangkuman materi kuliah Business Cloud Design tentang pengenalan cloud computing, karakteristik NIST, model layanan, deployment, dan hubungannya dengan open source berdasarkan slide pertemuan 1."
Bagian yang disesuaikan dari keluaran prompt ada pada: Menyederhanakan bahasa agar tidak terlalu kaku/baku, merapikan alur sejarah menjadi poin inti, membuang basa-basi pembuka AI, serta menyusun ulang bagian Open Source dan UU PDP agar lebih fokus ke alasan praktis di dunia bisnis.

---

# Catatan Kuliah: Paradigma Cloud Computing & Open Source

## 1. Apa itu Cloud Computing?
Secara sederhana, cloud computing adalah model penyediaan sumber daya komputasi (server, storage, jaringan, software) lewat internet. Kita tidak perlu lagi beli dan pasang server fisik sendiri di kantor; cukup sewa sesuai kebutuhan, pakai, lalu bayar apa yang dipakai.

Berdasarkan definisi **NIST** (*National Institute of Standards and Technology*), cloud computing memungkinkan akses jaringan yang fleksibel dan *on-demand* ke kumpulan sumber daya bersama yang bisa disiapkan dan dirilis secara cepat dengan usaha pengelolaan yang minimal.

## 2. Garis Waktu Perkembangan
* **1950-an:** Konsep awal *time-sharing system* pada komputer mainframe (digagas John McCarthy).
* **1961:** Muncul visi *Grid Computing*—komputer diprediksi bakal jadi kebutuhan publik seperti utilitas air atau listrik.
* **1969 & 1990:** Lahirnya ARPANET, lalu disusul penemuan World Wide Web (WWW) oleh Tim Berners-Lee yang memicu era *client-server*.
* **1997:** Istilah "Cloud Computing" mulai dipakai secara formal oleh Prof. Ramnath Chellappa.
* **1999:** Salesforce membuktikan aplikasi bisnis bisa diakses lewat web browser tanpa instalasi lokal (awal mula SaaS modern).
* **2002 - 2006:** AWS meluncurkan layanan komputasi komersial modern, disusul Amazon EC2 yang mempopulerkan IaaS.
* **2009 - sekarang:** Masuknya Google Cloud, Microsoft Azure, dan penyedia lokal, serta pergeseran ke kontainer dan microservices.

## 3. Karakteristik Utama Cloud (Standar NIST)
Ada 5 karakteristik dasar cloud yang membedakannya dari hosting tradisional, ditambah konsep multi-tenant:
1. **On-demand Self-Service:** Pengguna bisa langsung menyalakan server atau menambah storage sendiri lewat dashboard/portal tanpa harus menghubungi teknisi vendor.
2. **Broad Network Access:** Layanan bisa dibuka dari mana saja menggunakan berbagai macam perangkat (laptop, HP, tablet).
3. **Resource Pooling:** Sumber daya fisik dikumpulkan jadi satu untuk melayani banyak pelanggan secara bersamaan (*multi-tenancy*), tapi data antar-pelanggan tetap aman terpisah.
4. **Rapid Elasticity:** Kapasitas bisa naik atau turun secara instan sesuai kebutuhan saat itu (contoh: server otomatis bertambah saat trafik naik).
5. **Measured Service:** Pemakaian terpantau jelas (CPU, bandwidth, storage) sehingga pengguna membayar persis apa yang mereka gunakan (*pay-as-you-go*).
6. **Multitenancy:** Satu infrastruktur bersama yang melayani banyak pengguna/organisasi dengan jaminan isolasi keamanan data.

## 4. Kelebihan & Kekurangan Cloud
* **Kelebihan:**
  * Fleksibilitas biaya: Mengurangi belanja modal di awal (*Capex*) menjadi biaya bulanan/operasional (*Opex*).
  * Skalabilitas mudah dan kapasitas penyimpanan praktis tanpa batas.
  * Aksesibilitas universal dan fitur pemulihan (*backup/disaster recovery*) bawaan.
* **Kekurangan:**
  * Ketergantungan penuh pada koneksi internet.
  * Ada isu privasi/keamanan data pihak ketiga.
  * Risiko *downtime* di luar kendali perusahaan.
  * Biaya bisa tidak terkontrol jika manajemen penggunaan tidak diawasi (*bill shock*).

## 5. Model Layanan & Deployment
### Model Layanan
* **SaaS (Software as a Service):** Aplikasi langsung pakai untuk pengguna akhir lewat web browser (misal: Microsoft 365, Google Docs).
* **PaaS (Platform as a Service):** Lingkungan siap pakai untuk developer membuat dan menjalankan kode aplikasi tanpa pusing urusan OS/server (misal: AWS Elastic Beanstalk, Heroku).
* **IaaS (Infrastructure as a Service):** Penyewaan infrastruktur dasar seperti mesin virtual, storage, dan network untuk arsitek TI (misal: AWS EC2, Google Compute Engine).
* **XaaS (Everything as a Service):** Perluasan layanan lain yang dijadikan berbasis cloud, seperti BaaS, DaaS, NaaS, dsb.

### Model Deployment
* **Public Cloud:** Infrastruktur milik vendor yang dibagi pakai ke publik (AWS, GCP, Azure, Alibaba).
* **Private Cloud:** Lingkungan khusus yang hanya dipakai oleh satu organisasi demi kendali penuh.
* **Hybrid Cloud:** Gabungan antara private cloud dan public cloud.
* **Community Cloud:** Cloud yang dipakai bersama oleh beberapa organisasi dengan kebutuhan/regulasi yang sama.

*Penyedia lokal di Indonesia:* Biznet Gio, Telkom Telstra, Lintasarta.

## 6. Sisi Frontend & Backend pada Cloud
* **Frontend:** Komponen yang berinteraksi langsung dengan pengguna (tampilan UI dan pengalaman UX). Bentuknya bisa berupa aplikasi Web (React, Vue), Mobile (Android/iOS), Headless (CLI/API/curl), GUI, maupun TUI (console/terminal).
* **Backend:** Sisi logis dan pengolahan data di server, mencakup aplikasi, layanan/service, runtime, database, storage, dan infrastruktur.

## 7. Kenapa Cloud Butuh Open Source?
Open source memegang peranan krusial dalam ekosistem cloud:
1. **Fondasi Infrastruktur:** Hampir semua platform cloud dibangun di atas software open source (Linux, hypervisor KVM, Kubernetes). Tanpa open source, biaya lisensi software akan sangat mahal.
2. **Bebas Vendor Lock-in:** Standar terbuka memudahkan pemindahan aplikasi tanpa terikat ke satu vendor tertentu.
3. **Inovasi Cepat:** Organisasi bisa langsung memakai solusi open source, menjalankannya di cloud dalam hitungan menit, dan mempercepat waktu peluncuran produk ke pasar (*time-to-market*).
4. **Kedaulatan Data & Regulasi:** Pemanfaatan open source pada Private Cloud memudahkan kepatuhan terhadap aturan privasi nasional, seperti **UU Perlindungan Data Pribadi (UU PDP)**, karena data sensitif tetap berada dalam kendali penuh institusi sendiri.
