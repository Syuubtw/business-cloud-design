Materi Minggu 4: Ekonomi Private Cloud dan Capital Expenditure
Prompt: Rangkum materi ekonomi cloud, perbedaan CAPEX vs OPEX, perhitungan TCO dan unit economics, serta studi kasus kampus 5 tahun di mana biaya private cloud dan public cloud sama-sama bernilai Rp2,7 miliar.
Bagian yang disesuaikan dari keluaran prompt ada pada: Menjelaskan perbandingan finansial dengan bahasa yang sederhana tanpa rumus yang berbelit-belit, menguraikan studi kasus kampus 5 tahun secara runut, dan menyoroti kenapa biaya nominal yang sama tidak berarti kedua opsi itu setara.

---

CATATAN KULIAH: EKONOMI PRIVATE CLOUD DAN CAPITAL EXPENDITURE

1. KONSEP DASAR: CAPEX VS OPEX
Keputusan membangun infrastruktur TI selalu melibatkan dua model pengeluaran keuangan:
- CAPEX (Capital Expenditure): Biaya modal yang dikeluarkan di muka dalam jumlah besar untuk membeli aset fisik jangka panjang, seperti server, storage SAN, switch jaringan, genset, dan AC pendingin data center.
- OPEX (Operational Expenditure): Biaya operasional rutin yang dikeluarkan saat sistem berjalan, seperti tagihan listrik, internet, gaji admin, lisensi langganan bulanan, atau biaya sewa public cloud.

Arus Kas vs Depresiasi Akuntansi:
Membeli perangkat keras server tidak langsung dicatat sebagai kerugian penuh di bulan pertama, melainkan disusutkan secara bertahap:
Depresiasi Garis Lurus per Tahun = Harga Pembelian Aset dibagi Estimasi Umur Manfaat
Contoh: Membeli server seharga Rp600 juta untuk masa pakai 5 tahun berarti ada beban akuntansi depresiasi sebesar Rp120 juta per tahun. Namun secara arus kas (cash flow), uang tunai Rp600 juta sudah harus keluar di awal saat pembelian dilakukan.


2. PERBANDINGAN KARAKTERISTIK FINANSIAL

Dimensi Penilaian:
- Arus Kas:
  Private Cloud besar di awal (upfront cost besar).
  Public Cloud tersebar setiap bulan mengikuti pemakaian.
- Kapasitas:
  Private Cloud harus dibeli dan diestimasi di muka.
  Public Cloud fleksibel, bisa ditambah atau dikurangi kapan saja.
- Risiko Utilisasi:
  Private Cloud ditanggung sendiri jika kapasitas server menganggur.
  Public Cloud dialihkan sebagian besar ke pihak penyedia cloud.
- Tingkat Kendali:
  Private Cloud memberi kendali fisik dan konfigurasi penuh.
  Public Cloud mengikuti aturan dan katalog layanan dari penyedia.
- Tantangan Biaya:
  Private Cloud berisiko membeli kapasitas berlebih (overprovisioning).
  Public Cloud berisiko lonjakan tagihan jika konsumsi tidak terkontrol.


3. MENGHITUNG TOTAL COST OF OWNERSHIP (TCO)
TCO adalah total seluruh biaya yang dikeluarkan sepanjang siklus hidup sistem, bukan cuma harga beli barang di faktur awal:
TCO = Biaya Investasi Awal + Biaya Operasional Rutin + Biaya Risiko dan Akhir Masa Pakai

Komponen TCO yang sering terlewatkan:
- Biaya Tenaga Kerja (SDM): Gaji teknisi, biaya sertifikasi, dan jam kerja lembur tim internal.
- Kapasitas Menganggur (Idle): Server yang dibeli mahal tetapi utilisasi pemakaian hariannya sangat rendah.
- Biaya Risiko: Kerugian finansial saat sistem down atau insiden kehilangan data bisnis.
- Biaya Pengalihan (Exit Cost): Biaya transfer data keluar jika suatu saat ingin pindah penyedia layanan.


4. KONSEP UNIT ECONOMICS DAN DILEMA UTILISASI
Daripada hanya melihat total biaya miliaran rupiah, bisnis lebih mudah menilai efisiensi melalui Unit Economics:
- Biaya per VM per bulan
- Biaya infrastruktur per transaksi pelanggan
- Biaya sistem per mahasiswa atau pengguna aktif

Mengapa Utilisasi 100 Persen Bukan Hal yang Baik?
- Utilisasi terlalu rendah (di bawah 30 persen): Banyak kapasitas menganggur, biaya per unit jadi sangat mahal.
- Utilisasi ideal (70 sampai 80 persen): Efisien secara biaya, namun masih menyisakan ruang aman (headroom) untuk mengantisipasi lonjakan trafik mendadak dan kegagalan komponen.
- Jika utilisasi dipaksa mendekati 100 persen, sistem akan langsung lambat dan terancam crash begitu ada kenaikan trafik sedikit saja.


5. STUDI KASUS: PRIVATE CLOUD VS PUBLIC CLOUD UNTUK KAMPUS

Data Kebutuhan Kampus (Horizon Analisis 5 Tahun):
Kebutuhan: 120 VM ekuivalen, 80 TB Storage, Target ketersediaan 99,9 persen.

Opsi A (Private Cloud On-Premise):
- CAPEX awal (server, storage, implementasi): Rp1,2 Miliar
- OPEX tahunan (daya, maintenance, support): Rp300 Juta per tahun
- Total Biaya 5 Tahun = Rp1,2 Miliar + (5 x Rp300 Juta) = Rp2,7 Miliar

Opsi B (Public Cloud):
- Biaya migrasi awal: Rp100 Juta
- Biaya sewa cloud tahunan: Rp520 Juta per tahun
- Total Biaya 5 Tahun = Rp100 Juta + (5 x Rp520 Juta) = Rp2,7 Miliar

Analisis Kritis: Nominalnya Sama-Sama Rp2,7 Miliar, Lalu Pilih yang Mana?
Karena biaya akhirnya persis sama, keputusan harus dilihat dari faktor strategis lainnya:
1. Ketersediaan Dana Tunai: Apakah kampus memiliki dana kas tunai Rp1,2 Miliar langsung di awal? Jika tidak, mencicil lewat public cloud (Rp520 juta per tahun) jauh lebih aman bagi likuiditas keuangan institusi.
2. Kesiapan Staf TI: Apakah kampus punya tim sysadmin yang sanggup merawat server fisik 24 jam sehari? Jika tim terbatas, opsi public cloud mengurangi beban operasional pemeliharaan hardware.
3. Pola Beban Kampus: Beban sistem kampus sifatnya musiman (sangat tinggi saat KRS atau awal semester, lalu sepi saat libur semester). Pada public cloud, saat masa libur semester kapasitas server bisa diturunkan agar tagihan mengecil.
4. Analisis Sensitivitas: Jika pemakaian data membengkak atau nilai tukar dolar terhadap rupiah naik drastis, biaya public cloud bisa melonjak melampaui Rp2,7 Miliar.


6. RISIKO BIAYA YANG KERAP DIABAIKAN
- Technical Debt: Menghemat biaya di awal dengan membeli hardware bekas atau spesifikasi murah sering kali menimbulkan biaya perbaikan yang jauh lebih besar di kemudian hari.
- Skill dan Staffing: Ketergantungan pada personel kunci dan tingginya biaya melatih staf untuk mengelola private cloud.
- Vendor Lock-in: Keterikatan berlebih pada fitur unik satu penyedia sehingga biaya untuk bermigrasi keluar menjadi sangat mahal.
- Governance Lemah: Mesin virtual uji coba lupa dimatikan sehingga tagihan cloud terus berjalan tanpa ada pihak yang bertanggung jawab.
