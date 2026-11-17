Materi Minggu 1: Paradigma Cloud Computing dan Gerakan Open Source
AI yang digunakan: Google Gemini
Prompt: Tolong jelaskan secara ringkas konsep dasar cloud computing menurut NIST dan bagaimana kaitannya dengan teknologi open source dalam dunia bisnis.
Bagian yang disesuaikan dari keluaran prompt ada pada: Menyusun penjelasan konsep ke dalam poin catatan belajar mandiri, menambahkan garis waktu sejarah perkembangannya, serta merangkum relevansi kedaulatan data dan UU PDP.

---

CATATAN KULIAH: PARADIGMA CLOUD COMPUTING DAN OPEN SOURCE

1. APA ITU CLOUD COMPUTING?
Secara sederhana, cloud computing adalah model penyediaan sumber daya komputasi seperti server, storage, jaringan, dan software melalui internet. Kita tidak perlu lagi membeli dan memasang server fisik sendiri di kantor. Cukup menyewa sesuai kebutuhan, menggunakan layanannya, lalu membayar apa yang dipakai.

Berdasarkan definisi NIST (National Institute of Standards and Technology), cloud computing memungkinkan akses jaringan yang fleksibel dan on-demand ke kumpulan sumber daya bersama yang dapat disiapkan dan dirilis secara cepat dengan usaha pengelolaan yang minimal.


2. GARIS WAKTU PERKEMBANGAN
- Tahun 1950-an: Konsep awal time-sharing system pada komputer mainframe yang digagas oleh John McCarthy.
- Tahun 1961: Muncul visi Grid Computing, di mana komputer diprediksi akan menjadi utilitas publik layaknya air atau listrik.
- Tahun 1969 dan 1990: Lahirnya ARPANET, disusul penemuan World Wide Web (WWW) oleh Tim Berners-Lee yang mengawali era client-server.
- Tahun 1997: Istilah Cloud Computing mulai digunakan secara formal oleh Prof. Ramnath Chellappa.
- Tahun 1999: Salesforce membuktikan aplikasi bisnis dapat diakses lewat web browser tanpa instalasi lokal, menandai awal SaaS modern.
- Tahun 2002 sampai 2006: AWS meluncurkan layanan komputasi komersial modern, disusul Amazon EC2 yang mempopulerkan IaaS.
- Tahun 2009 hingga sekarang: Masuknya Google Cloud, Microsoft Azure, penyedia lokal, serta pergeseran ke kontainer dan microservices.


3. KARAKTERISTIK UTAMA CLOUD (STANDAR NIST)
Ada lima karakteristik dasar cloud yang membedakannya dari hosting tradisional, ditambah konsep multi-tenant:
1. On-demand Self-Service: Pengguna dapat langsung mengaktifkan server atau menambah penyimpanan sendiri lewat portal tanpa harus menghubungi teknisi penyedia layanan.
2. Broad Network Access: Layanan dapat diakses dari mana saja melalui berbagai macam perangkat seperti laptop, ponsel pintar, dan tablet.
3. Resource Pooling: Sumber daya fisik dikumpulkan menjadi satu untuk melayani banyak pelanggan secara bersamaan (multi-tenancy), dengan data antar-pelanggan yang tetap terisolasi dan aman.
4. Rapid Elasticity: Kapasitas dapat dinaikkan atau diturunkan seketika sesuai kebutuhan saat itu, misalnya server otomatis bertambah saat trafik meningkat.
5. Measured Service: Pemakaian sumber daya dipantau dan diukur dengan jelas sehingga pengguna hanya membayar apa yang benar-benar mereka gunakan (pay-as-you-go).
6. Multitenancy: Satu infrastruktur bersama yang melayani banyak penyewa dengan jaminan pemisahan data yang ketat.


4. KELEBIHAN DAN KEKURANGAN CLOUD
Kelebihan:
- Fleksibilitas biaya: Mengubah belanja modal di awal (Capex) menjadi biaya operasional rutin (Opex).
- Skalabilitas mudah dan kapasitas penyimpanan praktis tanpa batas.
- Aksesibilitas universal dari berbagai tempat serta fitur pencadangan data (backup dan disaster recovery) bawaan.

Kekurangan:
- Sangat bergantung pada ketersediaan koneksi internet.
- Adanya isu privasi dan keamanan data pihak ketiga.
- Risiko downtime yang berada di luar kendali perusahaan.
- Biaya kumulatif bisa membengkak jika manajemen penggunaan tidak diawasi dengan ketat.


5. MODEL LAYANAN DAN DEPLOYMENT
Model Layanan:
- SaaS (Software as a Service): Aplikasi langsung pakai untuk pengguna akhir lewat web browser, contohnya Microsoft 365 dan Google Docs.
- PaaS (Platform as a Service): Lingkungan siap pakai bagi developer untuk membuat dan menjalankan aplikasi tanpa mengurus OS atau server fisik, contohnya AWS Elastic Beanstalk dan Heroku.
- IaaS (Infrastructure as a Service): Penyewaan infrastruktur dasar seperti mesin virtual, storage, dan jaringan untuk arsitek TI, contohnya AWS EC2 dan Google Compute Engine.
- XaaS (Everything as a Service): Perluasan konsep layanan cloud ke berbagai bidang lain seperti BaaS, DaaS, dan NaaS.

Model Deployment:
- Public Cloud: Infrastruktur milik pihak ketiga yang dibagi pakai untuk publik (AWS, GCP, Azure, Alibaba).
- Private Cloud: Lingkungan khusus yang hanya digunakan oleh satu organisasi demi kendali penuh.
- Hybrid Cloud: Gabungan terintegrasi antara private cloud dan public cloud.
- Community Cloud: Cloud yang digunakan bersama oleh beberapa organisasi dengan kepentingan atau regulasi yang sama.

Penyedia cloud lokal di Indonesia antara lain: Biznet Gio, Telkom Telstra, dan Lintasarta.


6. SISI FRONTEND DAN BACKEND PADA CLOUD
- Frontend: Komponen antarmuka yang berinteraksi langsung dengan pengguna, berfokus pada UI (tampilan) dan UX (kenyamanan pengalaman pengguna). Bentuknya mencakup Web (React, Vue), Mobile (Android, iOS), Headless (CLI, API, curl), GUI, serta TUI (antarmuka teks terminal).
- Backend: Logika pemrosesan dan penyimpanan di sisi server, mencakup aplikasi, layanan, runtime, database, storage, dan infrastruktur fisik.


7. PERAN OPEN SOURCE DALAM CLOUD
Open source memegang peranan sangat penting dalam ekosistem cloud:
1. Fondasi Infrastruktur: Sebagian besar platform cloud dibangun di atas software open source seperti Linux, hypervisor KVM, dan Kubernetes.
2. Mencegah Vendor Lock-in: Standar terbuka memudahkan pemindahan aplikasi antar-platform tanpa terikat pada satu penyedia.
3. Inovasi Cepat: Organisasi dapat langsung memanfaatkan kode open source dan menjalankannya di cloud dalam hitungan menit, mempercepat peluncuran produk ke pasar.
4. Kedaulatan Data dan Regulasi: Pemanfaatan open source pada Private Cloud memudahkan institusi memenuhi aturan kepatuhan nasional, seperti UU Perlindungan Data Pribadi (UU PDP), karena kontrol data sensitif sepenuhnya berada di tangan organisasi sendiri.
