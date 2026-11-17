Materi Minggu 3: Private Cloud dan IT Alignment
Prompt: "Rangkum materi Private Cloud dan IT Alignment, jelaskan kenapa virtualisasi bukan otomatis private cloud, konsep showback vs chargeback, rantai alignment bisnis ke TI, serta jebakan umum seperti cloud-washing."
Bagian yang disesuaikan dari keluaran prompt ada pada: Mengubah penjelasan teori menjadi bahasa yang lebih lugas dan aplikatif, memperjelas perbedaan showback dan chargeback dengan bahasa yang praktis, serta merapikan poin studi kasus kampus dan 4 jebakan IT alignment.

---

# Catatan Kuliah: Private Cloud dan IT Alignment

## 1. Apa Itu Sebenarnya Private Cloud?
Private Cloud adalah lingkungan cloud yang didedikasikan secara eksklusif hanya untuk satu organisasi. Lokasi fisiknya tidak harus selalu di kantor sendiri (on-premises); bisa juga disewa di data center pihak ketiga (*hosted private cloud*), selama lingkungan dan kendalinya terisolasi khusus.

> **Poin Kunci:** Memiliki banyak server virtual belum tentu berarti sudah punya private cloud!

### Perbedaan Mendasar: Virtualisasi Biasa vs Private Cloud
* **Virtualisasi Murni:** Cuma sekadar membagi satu server fisik menjadi beberapa Virtual Machine (VM) agar hemat hardware. Pembuatan VM masih manual lewat tiket ke tim sysadmin.
* **Private Cloud:** Memiliki **lapisan layanan (*service layer*)**. Ada portal *self-service* (pengguna bisa minta VM/container sendiri dari katalog), otomasi konfigurasi, monitoring, serta tata kelola alokasi biaya.

### Konsep Showback vs Chargeback
Dua mekanisme untuk mengukur pemakaian sumber daya TI oleh divisi/unit bisnis:
* **Showback:** Biaya pemakaian server/storage hanya **ditunjukkan** ke unit bisnis yang memakai agar mereka sadar (*aware*) berapa biaya infrastruktur yang mereka konsumsi, tanpa benar-benar memotong anggaran divisi mereka.
* **Chargeback:** Biaya pemakaian benar-benar **ditagihkan** dan dipotong dari anggaran operasional divisi pemakai. Ini berguna agar divisi tidak asal-asalan meminta server kapasitas besar yang akhirnya menganggur.

---

## 2. Kapan Private Cloud Layak Dipilih?
Private cloud tidak selalu jadi pilihan terbaik karena butuh biaya investasi dan keahlian tim. Opsi ini layak jika:
1. **Regulasi & Kedaulatan Data:** Wajib menyimpan data sensitif di lingkungan tertutup sendiri (misal: perbankan atau instansi pemerintah).
2. **Pola Beban Kerja Stabil:** Beban trafik dapat diperkirakan sepanjang tahun, sehingga kapasitas hardware yang dibeli tidak banyak menganggur.
3. **Kebutuhan Platform Bersama:** Banyak tim internal membutuhkan standardisasi lingkungan kerja yang seragam.
4. **Kesiapan SDM Internal:** Perusahaan memiliki tim teknis yang siap mengelola infrastruktur secara berkelanjutan.

---

## 3. Rantai IT Alignment: Dari Sasaran Bisnis ke Operasi TI
Teknologi tidak boleh dibeli hanya karena tren, tetapi harus menjawab kebutuhan bisnis nyata:

$$\text{Strategi Bisnis} \longrightarrow \text{Kapabilitas TI} \longrightarrow \text{Arsitektur Cloud} \longrightarrow \text{Ukuran Hasil (KPI)}$$

* **Strategi Bisnis:** Ingin peluncuran fitur lebih cepat dan layanan pelanggan tidak sering macet.
* **Kapabilitas:** Butuh lingkungan uji coba aplikasi yang siap dalam hitungan menit dan sistem yang tahan gangguan.
* **Arsitektur:** Diterjemahkan ke penyediaan katalog kontainer, otomatisasi rilis, segmentasi jaringan, dan backup otomatis.
* **Ukuran Hasil (KPI):** Diukur dari waktu *provisioning*, ketersediaan (*availability*), dan kecepatan pemulihan insiden.

### 4 Sasaran Desain Utama:
1. **Cepat:** Otomasi *provisioning* mandiri tanpa alur birokrasi panjang.
2. **Andal:** Menentukan target **SLO** (*Service Level Objective*), redundansi server, dan pengujian berkala terhadap restore backup.
3. **Aman:** Menerapkan *Principle of Least Privilege* (hak akses secukupnya), pemisahan data sensitif, dan log audit.
4. **Efisien:** Memastikan pemakaian hardware optimal (*right-sizing*) dan VM yang sudah tidak dipakai langsung dimatikan (*lifecycle policy*).

---

## 4. Tata Kelola & Guardrails
Tata kelola (*governance*) yang baik bukan berarti memperlambat kerja tim dengan birokrasi, melainkan membuat **Guardrails**: aturan main otomatis yang menjaga sistem tetap aman dan patuh tanpa harus meminta izin manual setiap saat (misal: batas kuota otomatis per tim, template keamanan bawaan).

---

## 5. Indikator Kinerja (KPI): Jangan Cuma Mengukur Uptime!
Mengukur keberhasilan cloud tidak cukup hanya dengan uptime server (99%), karena server bisa saja menyala tapi aplikasinya error. Metrik harus melihat:
* **Kecepatan:** Berapa menit waktu yang dibutuhkan sejak pengguna meminta server hingga server siap pakai?
* **Keandalan:** Selain ketersediaan, perhatikan **MTTR** (*Mean Time to Repair* - waktu untuk memperbaiki sistem saat down) dan keberhasilan uji restore data.
* **Efisiensi:** Berapa persen utilisasi hardware nyata? Berapa kapasitas yang terbuang menganggur?
* **Kepatuhan:** Apakah semua VM rutin di-patch keamanannya?

---

## 6. Tahapan Implementasi (Roadmap)
1. **Discover:** Petakan aplikasi yang ada, data sensitif, pengguna, dan biaya operasional saat ini.
2. **Design:** Tentukan arsitektur awal, katalog layanan, guardrails keamanan, dan target SLO.
3. **Pilot:** Uji coba pada beberapa aplikasi percontohan untuk menguji performa dan prosedur backup.
4. **Scale:** Buka layanan ke seluruh unit kerja, terapkan otomasi menyeluruh, dan aktifkan showback/chargeback.

---

## 7. Empat Jebakan Umum dalam IT Alignment
1. **Technology-First:** Membeli perangkat keras atau lisensi canggih terlebih dahulu, baru kemudian bingung mau dipakai untuk apa.
2. **Ownership Kabur:** Tidak jelas siapa pejabat yang bertanggung jawab atas data, tagihan biaya, dan keamanan sistem.
3. **Cloud-Washing:** Menjuluki sistem virtualisasi lama sebagai "Private Cloud" padahal pelayanannya masih manual dan lambat.
4. **Metrics Theater:** Menyajikan laporan angka uptime tinggi demi formalitas, padahal pengguna bisnis sering mengeluhkan sistem lemot dan bermasalah.
