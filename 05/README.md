Materi Minggu 5: Metode Kuantitatif Ekonomi Infrastruktur untuk Deployment Cloud
AI yang digunakan: Google Gemini
Prompt: Bagaimana cara memahami analisis kuantitatif ekonomi infrastruktur cloud menggunakan metrik TCO, ROI, dan payback period?
Bagian yang disesuaikan dari keluaran prompt ada pada: Menyusun alur perhitungan rumus langkah demi langkah secara runut, menyederhanakan penjelasan skenario studi kasus, dan menambahkan catatan uji sensitivitas serta praktik FinOps.

---

CATATAN KULIAH: METODE KUANTITATIF EKONOMI INFRASTRUKTUR CLOUD

1. MENGAPA ANALISIS KUANTITATIF DIPERLUKAN?
Memilih antara membeli server sendiri (Private Cloud) atau menyewa layanan (Public Cloud) tidak boleh sekadar menebak atau ikut-ikutan tren. Keputusan harus didukung oleh angka dan analisis kuantitatif untuk melihat:
- Berapa total biaya riil sepanjang masa pakai sistem?
- Berapa manfaat finansial yang didapatkan organisasi?
- Berapa lama modal awal investasi bisa kembali (break-even point)?


2. ENAM KOMPONEN BIAYA INFRASTRUKTUR
Bukan cuma harga hardware atau biaya sewa bulanan, ada 6 komponen biaya yang harus diperhitungkan:
1. CAPEX: Pembelian awal server, rak, storage, dan switch jaringan.
2. OPEX: Tagihan listrik harian, pendingin ruangan, sewa koneksi internet, dan lisensi software.
3. People Cost: Gaji tim sysadmin, network engineer, database administrator, dan biaya pelatihan staf.
4. Transition Cost: Biaya migrasi data awal, penyesuaian aplikasi, dan masa uji coba sistem paralel.
5. Risk Cost: Kerugian finansial yang timbul saat sistem mati (downtime) atau insiden keamanan.
6. Exit Cost (Biaya Pengalihan): Biaya pemindahan data dan biaya transfer keluar (data egress fee) jika memutuskan berhenti berlangganan.


3. RUMUS METRIK FINANSIAL SEDERHANA

- TCO (Total Cost of Ownership):
  TCO = Biaya Awal + Total Biaya Operasi Kumulatif + Biaya Transisi + Biaya Risiko dan Keluar

- ROI Sederhana (Return on Investment):
  Mengukur persentase keuntungan relatif terhadap total biaya yang dikeluarkan:
  ROI = ((Total Manfaat dikurangi Total Biaya TCO) dibagi Total Biaya TCO) dikali 100 persen

- Payback Period:
  Waktu yang diperlukan agar manfaat bersih tahunan bisa menutup biaya investasi awal:
  Payback Period = Biaya Investasi dan Transisi di Awal dibagi Manfaat Bersih Tahunan


4. SIMULASI STUDI KASUS 3 TAHUN: PRIVATE VS PUBLIC CLOUD

Skenario Kasus:
Sebuah perusahaan menjalankan aplikasi ERP dan portal internal selama 3 tahun, dengan estimasi manfaat efisiensi bisnis sebesar Rp1.200 Juta per tahun (Total Manfaat 3 Tahun = Rp3.600 Juta).

Data Input Biaya (Juta Rupiah):
- Investasi Awal:
  Private Cloud Rp1.200 jt | Public Cloud Rp100 jt
- Operasi Infrastruktur per Tahun:
  Private Cloud Rp300 jt | Public Cloud Rp480 jt
- Tenaga Ahli per Tahun:
  Private Cloud Rp250 jt | Public Cloud Rp150 jt
- Migrasi dan Transisi (1x di awal):
  Private Cloud Rp150 jt | Public Cloud Rp200 jt
- Biaya Keluar atau Egress di Akhir:
  Private Cloud Rp0 jt | Public Cloud Rp80 jt

Perhitungan Langkah Demi Langkah:

1. Perhitungan TCO 3 Tahun
- Private Cloud:
  TCO = 1.200 + (300 x 3) + (250 x 3) + 150 = 1.200 + 900 + 750 + 150 = Rp3.000 Juta
- Public Cloud:
  TCO = 100 + (480 x 3) + (150 x 3) + 200 + 80 = 100 + 1.440 + 450 + 200 + 80 = Rp2.270 Juta
Kesimpulan TCO: Public cloud lebih murah Rp730 Juta (sekitar 24,3 persen) dibanding private cloud pada asumsi dasar ini.

2. Perhitungan ROI Sederhana
- Private Cloud:
  ROI = ((3.600 dikurangi 3.000) dibagi 3.000) x 100 persen = (600 dibagi 3.000) x 100 persen = 20,0 persen
- Public Cloud:
  ROI = ((3.600 dikurangi 2.270) dibagi 2.270) x 100 persen = (1.330 dibagi 2.270) x 100 persen = 58,6 persen

3. Perhitungan Payback Period
- Private Cloud:
  Modal Awal = 1.200 + 150 = Rp1.350 Juta
  Manfaat Bersih per Tahun = 1.200 dikurangi (300 + 250) = Rp650 Juta per tahun
  Payback Period = 1.350 dibagi 650 = 2,08 Tahun
- Public Cloud:
  Modal Awal = 100 + 200 = Rp300 Juta
  Manfaat Bersih per Tahun = 1.200 dikurangi (480 + 150) = Rp570 Juta per tahun
  Payback Period = 300 dibagi 570 = 0,53 Tahun (sekitar 6,4 bulan)


5. UJI SENSITIVITAS: BAGAIMANA JIKA BIAYA PUBLIC CLOUD MELONJAK?
Perhitungan di atas mengasumsikan kondisi stabil. Namun bagaimana jika biaya operasional public cloud ternyata membengkak 30 persen (misalnya akibat lonjakan pemakaian data dan kenaikan kurs dolar)?
- Biaya operasional public naik dari Rp480 jt menjadi Rp624 jt per tahun (+Rp144 jt per tahun).
- Tambahan biaya 3 tahun = 3 x Rp144 jt = Rp432 jt.
- TCO Public Baru = 2.270 + 432 = Rp2.702 Juta.
Dampak: Keunggulan penghematan public cloud menyusut dari Rp730 jt menjadi hanya Rp298 jt. Hal ini membuktikan pentingnya pengujian batas risiko sebelum mengambil keputusan final.


6. PENGENDALIAN BIAYA DENGAN FINOPS
Agar biaya cloud tidak bocor tak terkontrol, perusahaan perlu menerapkan praktik FinOps:
- Tagging: Memberi label jelas pada setiap mesin server virtual (milik departemen mana dan untuk keperluan apa).
- Right-sizing: Memilih kapasitas CPU dan RAM sesuai beban kerja riil, bukan memilih paket terbesar untuk jaga-jaga.
- Scheduling: Mengatur server pengujian agar otomatis mati di malam hari atau saat akhir pekan.
- Reserved Capacity: Mengikat kontrak komitmen 1 sampai 3 tahun untuk server yang sudah pasti dipakai terus-menerus demi mendapatkan diskon besar dari penyedia cloud.
