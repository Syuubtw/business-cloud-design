Materi Minggu 2: Model Layanan Cloud Computing
AI yang digunakan: Google Gemini
Prompt: Rangkum materi model layanan cloud computing (SaaS, PaaS, IaaS) beserta pembagian tanggung jawabnya, serta jelaskan layanan modern seperti NaaS, IDaaS, dan AIaaS secara terstruktur.
Bagian yang disesuaikan dari keluaran prompt ada pada: Mengubah gaya penulisan agar seperti catatan belajar mandiri, menyederhanakan tabel pembagian tanggung jawab (shared responsibility model) agar lebih ringkas, dan merangkum poin esensial dari NaaS, IDaaS, dan AIaaS tanpa jargon berulang.

---

CATATAN KULIAH: MODEL LAYANAN CLOUD COMPUTING

1. APA ITU CLOUD SERVICES?
Cloud Services adalah layanan teknologi informasi yang disediakan oleh vendor pihak ketiga lewat jaringan internet. Inti manfaatnya adalah organisasi tidak perlu berinvestasi membeli server fisik atau membangun fasilitas data center sendiri.

Nilai Utama untuk Bisnis:
- Elastisitas dan Skala: Kapasitas bisa ditambah seketika saat jumlah pengguna melonjak.
- Keamanan Terkelola: Standar keamanan tinggi yang dirawat langsung oleh tim ahli vendor.
- Efisiensi Biaya: Membayar sesuai yang dikonsumsi (pay-per-use) tanpa membebani biaya perawatan fisik.
- Kecepatan Rilis: Tidak perlu menunggu berbulan-bulan untuk pengadaan perangkat keras baru.


2. TIGA MODEL LAYANAN UTAMA DAN PEMBAGIAN TANGGUNG JAWAB

Perbedaan utama ketiga model ini terletak pada siapa yang bertanggung jawab mengurus tiap lapisan sistem:

Tabel Pembagian Tanggung Jawab (Shared Responsibility):
- Lapisan Aplikasi dan Data:
  On-Premises diurus sendiri, IaaS diurus sendiri, PaaS diurus sendiri, SaaS diurus vendor.
- Lapisan Runtime dan Middleware:
  On-Premises diurus sendiri, IaaS diurus sendiri, PaaS diurus vendor, SaaS diurus vendor.
- Lapisan Sistem Operasi (OS):
  On-Premises diurus sendiri, IaaS diurus sendiri, PaaS diurus vendor, SaaS diurus vendor.
- Lapisan Virtualisasi dan Server Fisik:
  On-Premises diurus sendiri, IaaS diurus vendor, PaaS diurus vendor, SaaS diurus vendor.
- Lapisan Storage dan Jaringan:
  On-Premises diurus sendiri, IaaS diurus vendor, PaaS diurus vendor, SaaS diurus vendor.


3. PEMBAHASAN MASING-MASING MODEL

A. Software as a Service (SaaS)
- Konsep: Layanan perangkat lunak siap pakai yang diakses langsung lewat web browser oleh pengguna akhir (end-user). Kita tinggal memakai tanpa perlu instalasi atau memikirkan update versi aplikasi.
- Contoh: Google Docs, Google Workspace, Microsoft 365, Dropbox, Slack, Trello, GitHub.
- Kelebihan: Praktis, tidak memerlukan perawatan teknis dari pengguna, dapat diakses dari mana saja.
- Kekurangan: Bergantung pada koneksi internet, fitur terbatas pada apa yang disediakan vendor, dan data disimpan di server pihak ketiga.

B. Platform as a Service (PaaS)
- Konsep: Layanan yang menyediakan lingkungan lengkap (OS, web server, database, runtime bahasa pemrograman) bagi programmer untuk membuat, menguji, dan merilis aplikasi.
- Kunci Teknologi: Banyak memanfaatkan teknologi kontainer (Docker) dan orkestrasi (Kubernetes) di balik layar.
- Varian PaaS: Termasuk CPaaS (Communication Platform seperti API SMS atau panggilan suara) dan MPaaS (Mobile Platform).
- Contoh: AWS Elastic Beanstalk, Google App Engine, Red Hat OpenShift, Heroku, Mendix.
- Kelebihan: Proses development jauh lebih cepat karena tim fokus menulis kode aplikasi saja tanpa pusing urusan server.
- Kekurangan: Ada risiko vendor lock-in, yaitu aplikasi bisa sulit dipindahkan jika terlalu terikat pada pustaka atau API eksklusif milik vendor tertentu.

C. Infrastructure as a Service (IaaS)
- Konsep: Penyewaan sumber daya perangkat keras virtual murni seperti mesin virtual (VM), vCPU, RAM, block storage, dan jaringan virtual. Pengguna memiliki kendali penuh atas sistem operasi dan software yang dipasang di atasnya.
- Contoh: Amazon EC2, Google Compute Engine, Azure Virtual Machines.
- Kelebihan: Fleksibilitas konfigurasi paling tinggi dan bebas mengatur arsitektur sistem sendiri.
- Kekurangan: Membutuhkan keahlian teknis (sysadmin atau DevOps) untuk instalasi OS, patch keamanan berkala, dan konfigurasi jaringan.


4. MODEL LAYANAN MODERN LAINNYA

1. Network as a Service (NaaS)
Fungsi dan infrastruktur jaringan yang disediakan sebagai layanan cloud tanpa organisasi harus membeli router, firewall fisik, atau switch mahal.
Cakupannya meliputi: VPN perusahaan, SD-WAN (Software-Defined WAN), bandwidth on-demand, firewall terkelola, dan proteksi IDS/IPS.

2. Identity as a Service (IDaaS)
Layanan manajemen identitas dan hak akses (Identity and Access Management / IAM) berbasis cloud.
Manfaatnya antara lain: Pengguna cukup memiliki satu akun untuk semua aplikasi kantor lewat SSO (Single Sign-On), diperkuat dengan verifikasi ganda MFA (Multi-Factor Authentication), dan pengaturan hak akses berbasis peran kerja (RBAC). Admin tidak perlu mengelola database login yang terpisah-pisah.

3. Artificial Intelligence as a Service (AIaaS)
Penyediaan kapabilitas kecerdasan buatan dan machine learning siap pakai melalui API atau platform terkelola.
Masalah yang dipecahkan: Mesin akselerator AI (GPU dan TPU) harganya sangat mahal, dan pipeline data rumit dibuat dari nol.
Bentuk layanannya berupa: Model pre-trained siap panggil (pengenalan suara, computer vision, pemrosesan teks dan bahasa), serta tool pelatihan model otomatis (AutoML).

4. Layanan Pendukung Tambahan (XaaS)
- DRaaS (Disaster Recovery as a Service): Layanan replikasi sistem cadangan yang langsung aktif saat pusat data utama bermasalah.
- DaaS (Desktop as a Service): Virtual desktop jarak jauh yang bisa dibuka staf dari perangkat apa saja secara aman.
- SecaaS (Security as a Service): Layanan keamanan siber terkelola seperti pemindaian kerentanan dan monitoring ancaman berkala.
