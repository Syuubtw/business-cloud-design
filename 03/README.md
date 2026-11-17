Materi Minggu 3: Private Cloud dan IT Alignment
AI yang digunakan: Google Gemini
Prompt: Rangkum materi Private Cloud dan IT Alignment, jelaskan kenapa virtualisasi bukan otomatis private cloud, konsep showback vs chargeback, rantai alignment bisnis ke TI, serta jebakan umum seperti cloud-washing.
Bagian yang disesuaikan dari keluaran prompt ada pada: Mengubah penjelasan teori menjadi bahasa yang lebih lugas dan aplikatif, memperjelas perbedaan showback dan chargeback dengan bahasa yang praktis, serta merapikan poin studi kasus kampus dan 4 jebakan IT alignment.

---

CATATAN KULIAH: PRIVATE CLOUD DAN IT ALIGNMENT

1. APA ITU SEBENARNYA PRIVATE CLOUD?
Private Cloud adalah lingkungan cloud yang didedikasikan secara eksklusif hanya untuk satu organisasi. Lokasi fisiknya tidak harus selalu di kantor sendiri (on-premises); bisa juga disewa di data center pihak ketiga (hosted private cloud), selama lingkungan dan kendalinya terisolasi khusus.

Poin Kunci: Memiliki banyak server virtual belum tentu berarti sudah memiliki private cloud.

Perbedaan Mendasar Virtualisasi Biasa vs Private Cloud:
- Virtualisasi Murni: Hanya sekadar membagi satu server fisik menjadi beberapa Virtual Machine (VM) agar menghemat hardware. Pembuatan VM masih dilakukan secara manual lewat tiket pengajuan ke tim sysadmin.
- Private Cloud: Memiliki lapisan layanan (service layer). Terdapat portal self-service di mana pengguna bisa meminta VM atau kontainer sendiri dari katalog yang disediakan, ada otomatisasi konfigurasi, monitoring berkala, serta tata kelola alokasi biaya.

Konsep Showback vs Chargeback:
Dua mekanisme untuk mengukur pemakaian sumber daya TI oleh divisi atau unit bisnis:
- Showback: Biaya pemakaian server atau storage hanya ditunjukkan ke unit bisnis yang memakai agar mereka sadar (aware) berapa biaya infrastruktur yang mereka konsumsi, tanpa benar-benar memotong anggaran divisi mereka.
- Chargeback: Biaya pemakaian benar-benar ditagihkan dan dipotong dari anggaran operasional divisi pemakai. Ini berguna agar divisi tidak sembarangan meminta server berkapasitas besar yang akhirnya menganggur.


2. KAPAN PRIVATE CLOUD LAYAK DIPILIH?
Private cloud tidak selalu jadi pilihan terbaik karena membutuhkan biaya investasi dan keahlian tim teknis. Opsi ini layak jika:
1. Regulasi dan Kedaulatan Data: Kewajiban menyimpan data sensitif di lingkungan tertutup sendiri (misal pada industri perbankan atau instansi pemerintah).
2. Pola Beban Kerja Stabil: Beban trafik dapat diperkirakan sepanjang tahun, sehingga kapasitas hardware yang dibeli tidak banyak menganggur.
3. Kebutuhan Platform Bersama: Banyak tim internal membutuhkan standardisasi lingkungan kerja yang seragam.
4. Kesiapan SDM Internal: Perusahaan memiliki tim teknis yang siap mengelola infrastruktur secara berkelanjutan.


3. RANTAI IT ALIGNMENT: DARI SASARAN BISNIS KE OPERASI TI
Teknologi tidak boleh dibeli hanya karena tren, tetapi harus menjawab kebutuhan bisnis nyata:

Strategi Bisnis -> Kapabilitas TI -> Arsitektur Cloud -> Ukuran Hasil (KPI)

- Strategi Bisnis: Contohnya ingin peluncuran fitur aplikasi lebih cepat dan layanan pelanggan tidak sering terganggu.
- Kapabilitas: Membutuhkan lingkungan uji coba aplikasi yang siap dalam hitungan menit dan sistem yang tahan gangguan.
- Arsitektur: Diterjemahkan ke penyediaan katalog kontainer, otomatisasi rilis, segmentasi jaringan, dan backup otomatis.
- Ukuran Hasil (KPI): Diukur dari waktu penyediaan (provisioning time), tingkat ketersediaan (availability), dan kecepatan pemulihan insiden.

Empat Sasaran Desain Utama:
1. Cepat: Otomasi provisioning mandiri tanpa alur birokrasi yang berbelit-belit.
2. Andal: Menentukan target SLO (Service Level Objective), redundansi server, dan pengujian berkala terhadap restore backup.
3. Aman: Menerapkan prinsip least privilege (hak akses secukupnya), pemisahan data sensitif, dan pencatatan log audit.
4. Efisien: Memastikan pemakaian hardware optimal (right-sizing) dan VM yang sudah selesai dipakai langsung dimatikan (lifecycle policy).


4. TATA KELOLA DAN GUARDRAILS
Tata kelola (governance) yang baik bukan berarti memperlambat kerja tim dengan birokrasi, melainkan membuat Guardrails: aturan main otomatis yang menjaga sistem tetap aman dan patuh tanpa harus meminta izin manual setiap saat, seperti penetapan batas kuota otomatis per tim dan template keamanan bawaan.


5. INDIKATOR KINERJA (KPI): JANGAN HANYA MENGUKUR UPTIME
Mengukur keberhasilan cloud tidak cukup hanya dengan uptime server (misalnya 99%), karena server bisa saja menyala tetapi aplikasinya mengalami galat. Metrik harus melihat:
- Kecepatan: Berapa menit waktu yang dibutuhkan sejak pengguna meminta server hingga server benar-benar siap pakai.
- Keandalan: Selain ketersediaan, perhatikan MTTR (Mean Time to Repair, yaitu waktu untuk memperbaiki sistem saat down) dan keberhasilan uji restore data.
- Efisiensi: Berapa persen utilisasi hardware nyata dan berapa kapasitas yang terbuang menganggur.
- Kepatuhan: Apakah seluruh VM rutin diperbarui patch keamanannya.


6. TAHAPAN IMPLEMENTASI (ROADMAP)
1. Discover: Memetakan aplikasi yang ada, data sensitif, pengguna, dan biaya operasional saat ini.
2. Design: Menentukan arsitektur awal, katalog layanan, guardrails keamanan, dan target SLO.
3. Pilot: Melakukan uji coba pada beberapa aplikasi percontohan untuk menguji performa dan prosedur backup.
4. Scale: Membuka layanan ke seluruh unit kerja, menerapkan otomasi menyeluruh, dan mengaktifkan showback atau chargeback.


7. EMPAT JEBAKAN UMUM DALAM IT ALIGNMENT
1. Technology-First: Membeli perangkat keras atau lisensi canggih terlebih dahulu, baru kemudian bingung mau dipakai untuk apa.
2. Ownership Kabur: Tidak jelas siapa penanggung jawab atas data, tagihan biaya, dan keamanan sistem.
3. Cloud-Washing: Menjuluki sistem virtualisasi lama sebagai Private Cloud padahal pelayanannya masih manual dan lambat.
4. Metrics Theater: Menyajikan laporan angka uptime tinggi demi formalitas, padahal pengguna bisnis sering mengeluhkan sistem lemot dan bermasalah.
