Materi Minggu 2: Model Layanan Cloud Computing
Prompt: "Rangkum materi model layanan cloud computing (SaaS, PaaS, IaaS) beserta pembagian tanggung jawabnya, serta jelaskan layanan modern seperti NaaS, IDaaS, dan AIaaS secara terstruktur."
Bagian yang disesuaikan dari keluaran prompt ada pada: Mengubah gaya penulisan agar seperti catatan belajar mandiri, menyederhanakan tabel pembagian tanggung jawab (shared responsibility model) agar lebih ringkas, dan merangkum poin esensial dari NaaS, IDaaS, dan AIaaS tanpa jargon berulang.

---

# Catatan Kuliah: Model Layanan Cloud Computing

## 1. Apa itu Cloud Services?
Cloud Services adalah layanan teknologi informasi yang disediakan oleh vendor pihak ketiga lewat jaringan internet. Inti manfaatnya adalah organisasi tidak perlu berinvestasi beli server fisik atau membangun data center sendiri.

### Nilai Utama untuk Bisnis:
* **Elastisitas & Skala:** Kapasitas bisa ditambah seketika saat pengguna melonjak.
* **Keamanan Terkelola:** Standar keamanan tinggi yang dirawat langsung oleh tim ahli vendor.
* **Efisiensi Biaya:** Membayar sesuai yang dikonsumsi (*pay-per-use*) tanpa membebani biaya perawatan fisik.
* **Kecepatan Rilis:** Tidak perlu nunggu berbulan-bulan untuk pengadaan perangkat keras baru.

---

## 2. Tiga Model Layanan Utama & Pembagian Tanggung Jawab

Perbedaan utama ketiga model ini terletak pada **siapa yang bertanggung jawab mengurus tiap lapisan sistem**:

| Lapisan Sistem | On-Premises (Server Sendiri) | IaaS (Infrastruktur) | PaaS (Platform) | SaaS (Software) |
| :--- | :---: | :---: | :---: | :---: |
| **Aplikasi & Data** | Kita urus sendiri | Kita urus sendiri | Kita urus sendiri | Diurus Vendor |
| **Runtime & Middleware** | Kita urus sendiri | Kita urus sendiri | Diurus Vendor | Diurus Vendor |
| **Sistem Operasi (OS)** | Kita urus sendiri | Kita urus sendiri | Diurus Vendor | Diurus Vendor |
| **Virtualisasi & Hardware** | Kita urus sendiri | Diurus Vendor | Diurus Vendor | Diurus Vendor |
| **Storage & Jaringan** | Kita urus sendiri | Diurus Vendor | Diurus Vendor | Diurus Vendor |

---

## 3. Pembahasan Masing-Masing Model

### A. Software as a Service (SaaS)
* **Konsep:** Layanan aplikasi siap pakai yang diakses langsung lewat web browser oleh pengguna akhir (*end-user*). Kita tinggal pakai tanpa perlu instalasi atau mikirin update versi.
* **Contoh:** Google Docs / Google Workspace, Microsoft 365, Dropbox, Slack, Trello, GitHub.
* **Plus:** Praktis, tidak perlu perawatan teknis, bisa diakses dari mana saja.
* **Minus:** Tergantung koneksi internet, fitur terbatas pada apa yang disediakan vendor, dan data disimpan di pihak ketiga.

### B. Platform as a Service (PaaS)
* **Konsep:** Layanan yang menyediakan lingkungan lengkap (OS, web server, database, runtime bahasa pemrograman) bagi programmer untuk membuat, menguji, dan merilis aplikasi.
* **Kunci Teknologi:** Banyak memanfaatkan teknologi kontainer (Docker) dan orkestrasi (Kubernetes) di balik layar.
* **Varian PaaS:** Termasuk CPaaS (*Communication Platform* seperti API SMS/Voice) dan MPaaS (*Mobile Platform*).
* **Contoh:** AWS Elastic Beanstalk, Google App Engine, Red Hat OpenShift, Heroku, Mendix.
* **Plus:** Proses development jauh lebih cepat karena tim fokus nulis kode aplikasi saja.
* **Minus:** Ada risiko *vendor lock-in* (aplikasi bisa susah dipindah jika memakai library eksklusif milik vendor tertentu).

### C. Infrastructure as a Service (IaaS)
* **Konsep:** Penyewaan sumber daya perangkat keras virtual murni (mesin virtual, vCPU, RAM, block storage, dan jaringan virtual). Pengguna punya kendali penuh atas sistem operasi dan software yang mau dipasang di atasnya.
* **Contoh:** Amazon EC2, Google Compute Engine, Azure Virtual Machines.
* **Plus:** Fleksibilitas konfigurasi paling tinggi, bebas atur arsitektur sendiri.
* **Minus:** Butuh keahlian teknis (*sysadmin/DevOps*) untuk instalasi OS, patch keamanan, dan konfigurasi jaringan.

---

## 4. Model Layanan Modern: NaaS, IDaaS, dan AIaaS

Selain tiga model klasik di atas, sekarang berkembang berbagai model layanan spesifik:

### 1. Network as a Service (NaaS)
Fungsi dan infrastruktur jaringan yang disediakan sebagai layanan cloud tanpa organisasi harus beli router, firewall fisik, atau switch mahal.
* **Cakupan:** VPN perusahaan, SD-WAN (*Software-Defined WAN*), *bandwidth on-demand*, firewall terkelola, dan proteksi IDS/IPS.

### 2. Identity as a Service (IDaaS)
Layanan manajemen identitas dan hak akses (*Identity & Access Management* / IAM) berbasis cloud.
* **Manfaat:** Pengguna cukup punya satu akun untuk semua aplikasi kantor lewat **SSO** (*Single Sign-On*), diperkuat dengan **MFA** (*Multi-Factor Authentication*), dan pengaturan hak akses berbasis peran (**RBAC**). Admin tidak perlu mengelola database login yang terpisah-pisah.

### 3. Artificial Intelligence as a Service (AIaaS)
Penyediaan kapabilitas kecerdasan buatan dan machine learning siap pakai melalui API atau platform terkelola.
* **Masalah yang Dipecahkan:** Mesin akselerator AI (GPU/TPU) harganya sangat mahal, dan pipeline data rumit dibuat dari nol.
* **Bentuk Layanan:** Model *pre-trained* siap panggil (seperti pengenalan suara, computer vision, NLP/LLM), serta tool pelatihan model otomatis (*AutoML*).

### 4. Layanan Pendukung Lainnya (*XaaS*)
* **DRaaS (Disaster Recovery as a Service):** Layanan replikasi sistem cadangan yang langsung aktif saat pusat data utama bermasalah.
* **DaaS (Desktop as a Service):** Virtual desktop jarak jauh yang bisa dibuka staf dari perangkat apa saja.
* **SecaaS (Security as a Service):** Layanan keamanan siber terkelola seperti scanning kerentanan dan monitoring ancaman berkala.
