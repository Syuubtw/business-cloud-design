# Rangkuman Perkuliahan Business Cloud Design

**Materi Minggu 1: Paradigma Cloud Computing dan Gerakan Open Source**  
**Prompt:**  
> "Tolong buatkan rangkuman komprehensif untuk materi kuliah Business Cloud Design Pertemuan 1 dengan topik 'Paradigma Cloud Computing dan Gerakan Open Source'. Rangkuman harus mencakup: definisi Cloud Computing menurut NIST, sejarah perkembangan dari era mainframe hingga modern, karakteristik esensial cloud dan multitenancy, kelebihan dan kekurangan cloud computing, model layanan (SaaS, PaaS, IaaS, XaaS), model deployment (Public, Private, Hybrid, Community), lanskap provider global dan lokal, perbandingan Frontend vs Backend dalam arsitektur cloud, teknologi container (Docker) dan orkestrasi (Kubernetes), serta analisis bagaimana sinergi Cloud Computing dan Open Source menciptakan Business Value Added bagi organisasi, termasuk kepatuhan regulasi UU PDP."

**Bagian yang disesuaikan dari keluaran prompt ada pada:**  
1. Menyelaraskan definisi NIST agar sesuai dengan terminologi baku yang dipelajari pada slide perkuliahan S1 Sistem Informasi UTDI.  
2. Memperdalam uraian pada 5 karakteristik esensial NIST ditambah konsep multitenancy terkait isolasi data penyewa.  
3. Memperinci aspek *Business Value Added* dari kolaborasi Open Source dan Cloud Computing, khususnya pada kedaulatan data (*data sovereignty*) dan kepatuhan terhadap UU Pelindungan Data Pribadi (UU PDP).  
4. Menambahkan elaborasi arsitektur frontend (UI/UX, Headless, TUI, GUI) dan backend yang selaras dengan bahasan slide.

---

## 1. Pengertian Cloud Computing (Definisi NIST)
Berdasarkan *National Institute of Standards and Technology* (NIST SP 800-145):
> *"Cloud Computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction."*

Secara praktis, cloud computing adalah model komputasi yang memungkinkan akses jaringan yang mudah dan fleksibel ke sumber daya komputasi bersama (server, penyimpanan, aplikasi, jaringan) yang dapat disediakan (*provisioned*) dan dirilis secara cepat dengan interaksi minimal dari penyedia layanan.

---

## 2. Sejarah Singkat Perkembangan Cloud Computing
* **1950-an:** Era *Mainframe*. John McCarthy menggagas *theory of time-sharing system*.
* **1961:** John McCarthy memprediksi bahwa komputasi suatu saat akan menjadi utilitas publik seperti air dan listrik (*Grid Computing*).
* **1969:** Kemunculan ARPANET sebagai cikal bakal internet.
* **1990:** Kelahiran *World Wide Web* (WWW) oleh Tim Berners-Lee yang mengawali era *Client-Server Computing*.
* **1997:** Istilah *Cloud Computing* pertama kali digunakan secara akademis oleh Prof. Ramnath Chellappa (Emory University).
* **1999:** Peluncuran Salesforce.com sebagai pelopor aplikasi bisnis berbasis SaaS melalui peramban web.
* **2002 – 2006:** Amazon meluncurkan AWS dan Amazon EC2 (Elastic Compute Cloud) yang mempopulerkan IaaS komersial.
* **2009:** Peluncuran Google Cloud Platform (GCP) dan ekspansi cloud hyperscaler global.

---

## 3. Karakteristik Esensial Cloud Computing
1. **On-demand Self-Service:** Konsumen dapat meminta dan memperoleh sumber daya komputasi (server, storage) secara otomatis tanpa interaksi manual manusia dengan vendor.
2. **Broad Network Access:** Kapabilitas komputasi dapat diakses melalui jaringan menggunakan mekanisme standar dari berbagai perangkat (laptop, smartphone, tablet, workstation).
3. **Resource Pooling:** Sumber daya komputasi milik penyedia dikumpulkan untuk melayani banyak pelanggan (*multi-tenant*) menggunakan model dinamis dengan alokasi fisik dan virtual.
4. **Rapid Elasticity:** Kapasitas dapat ditambah atau dikurangi secara elastis dan cepat sesuai fluktuasi permintaan beban kerja (*workload*).
5. **Measured Service:** Penggunaan sumber daya dimonitor, dikontrol, dan dilaporkan secara transparan melalui sistem penagihan berbasis konsumsi (*pay-as-you-go*).
6. **Multitenancy:** Satu arsitektur fisik atau logis melayani banyak penyewa (*tenant*), di mana data dan proses tiap tenant diisolasi secara ketat dan aman.

---

## 4. Kelebihan dan Kekurangan Cloud Computing
### Kelebihan
* **Ekonomis & Fleksibel:** Mengubah biaya kapital besar (*Capex*) menjadi biaya operasional (*Opex*) dengan berbagai model harga (langganan, per jam/detik, *spot/transient instance*).
* **Kapasitas Penyimpanan Tak Terbatas:** Kemudahan menambah kapasitas storage sesuai kebutuhan bisnis.
* **Akses Universal:** Aksesibilitas layanan dari mana saja selama terhubung jaringan internet.
* **Skalabilitas:** Kemampuan meningkatkan atau menurunkan performa sistem secara instan.
* **Keandalan & Pemulihan:** Ketersediaan mekanisme *redundancy*, *backup*, dan *disaster recovery*.

### Kekurangan
* Ketergantungan mutlak pada stabilitas koneksi internet.
* Potensi risiko privasi dan keamanan data (*data sovereignty*).
* Potensi *downtime* di luar kendali organisasi.
* Biaya kumulatif yang berisiko membengkak jika tata kelola konsumsi tidak dipantau secara ketat.

---

## 5. Model Layanan Cloud Computing
1. **SaaS (Software as a Service):** Layanan aplikasi siap pakai yang ditujukan langsung untuk *end-user* melalui web/aplikasi (contoh: Microsoft 365, Google Docs, Gmail).
2. **PaaS (Platform as a Service):** Lingkungan pengembangan dan deployment aplikasi yang ditujukan untuk pengembang (*developers*) tanpa perlu mengelola OS dan infrastruktur bawahnya (contoh: AWS Elastic Beanstalk, Google App Engine, OpenShift).
3. **IaaS (Infrastructure as a Service):** Layanan infrastruktur dasar berupa mesin virtual (VM), komputasi, storage, dan jaringan yang dikelola oleh *network/infrastructure architects* (contoh: AWS EC2, Google Compute Engine, OpenStack).
4. **XaaS (*Everything as a Service*):** Perluasan model cloud untuk berbagai kapabilitas lain, seperti *Backend as a Service* (BaaS), *Data as a Service* (DaaS), *Network as a Service* (NaaS), dan *Identity as a Service* (IDaaS).

---

## 6. Model Deployment Cloud Computing
* **Public Cloud:** Infrastruktur dimiliki dan dikelola oleh penyedia pihak ketiga untuk publik/multi-organisasi.
* **Private Cloud (On-Premise / Hosted):** Infrastruktur didedikasikan secara eksklusif untuk satu organisasi dengan kontrol penuh.
* **Hybrid Cloud:** Kombinasi yang mengintegrasikan private cloud dan public cloud dengan orkestrasi dan portabilitas data.
* **Community Cloud:** Infrastruktur yang digunakan bersama oleh beberapa organisasi yang memiliki kepentingan atau regulasi serupa.

**Lanskap Penyedia Layanan:**
* *Global:* Amazon Web Services (AWS), Google Cloud Platform (GCP), Microsoft Azure, Alibaba Cloud, IBM Cloud, Oracle Cloud.
* *Lokal (Indonesia):* Biznet Gio, Telkom / Telkomtelstra, Lintasarta.

---

## 7. Arsitektur Komponen: Frontend dan Backend
* **Frontend:** Komponen antarmuka pengguna yang berfokus pada **UI** (keindahan dan tata letak tampilan) dan **UX** (kemudahan dan kepuasan pengalaman pengguna). Mencakup aplikasi Web (Vue, React, Angular), Mobile (Native/Hybrid), GUI, TUI (*Text User Interface*), dan Headless (CLI, curl, API).
* **Backend:** Lapisan logika bisnis, manajemen layanan, keamanan, runtime eksekusi, database, dan infrastruktur penyimpanan data yang berjalan di cloud.

---

## 8. Peran Container (Docker) dan Orkestrasi (Kubernetes)
* **Teknologi Kontainer (Docker):** Mengemas aplikasi dan pustakanya ke dalam *container image* yang ringan, konsisten, dan dapat dijalankan di lingkungan mana pun tanpa *overhead* sistem operasi penuh.
* **Orkestrasi (Docker Swarm / Kubernetes):** Mengelola klaster kontainer, menangani *auto-healing*, distribusi beban (*load balancing*), serta penskalaan otomatis di atas infrastruktur IaaS/PaaS.

---

## 9. Sinergi Cloud Computing dan Open Source Menciptakan Business Value Added
1. **Pondasi Teknologi Bebas Vendor Lock-in:** Sebagian besar infrastruktur cloud modern dibangun di atas fondasi open source (Linux, KVM, Kubernetes), memberikan fleksibilitas arsitektur tanpa terkunci vendor tertentu.
2. **Katalis Inovasi Cepat (*Time-to-Market*):** Menggabungkan pustaka open source dengan infrastruktur cloud memungkinkan organisasi bereksperimen dan meluncurkan produk dalam hitungan menit tanpa investasi awal perangkat keras yang mahal.
3. **Kedaulatan Data (*Data Sovereignty*) & Kepatuhan Hukum:** Pemanfaatan teknologi open source di lingkungan *Private Cloud* memungkinkan institusi publik, perbankan, dan universitas mematuhi regulasi privasi data nasional (**UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi / UU PDP**) sekaligus memangkas biaya lisensi perangkat lunak proprietary.
4. **Efek Domino:** Komunitas open source memproduksi inovasi $\rightarrow$ Penyedia cloud mengemasnya menjadi layanan siap pakai $\rightarrow$ Bisnis memanfaatkan layanan untuk menciptakan diferensiasi nilai tanpa risiko finansial berlebih.
