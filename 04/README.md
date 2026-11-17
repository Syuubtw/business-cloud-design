Materi Minggu 4: Ekonomi Private Cloud dan Capital Expenditure
Prompt: "Rangkum materi ekonomi cloud, perbedaan CAPEX vs OPEX, perhitungan TCO dan unit economics, serta studi kasus kampus 5 tahun di mana biaya private cloud dan public cloud sama-sama bernilai Rp2,7 miliar."
Bagian yang disesuaikan dari keluaran prompt ada pada: Menjelaskan perbandingan finansial dengan bahasa yang sederhana tanpa rumus yang berbelit-belit, menguraikan studi kasus kampus 5 tahun secara runut, dan menyoroti kenapa biaya nominal yang sama tidak berarti kedua opsi itu setara.

---

# Catatan Kuliah: Ekonomi Private Cloud & Capital Expenditure

## 1. Konsep Dasar: CAPEX vs OPEX
Keputusan membangun infrastruktur TI selalu melibatkan dua model pengeluaran keuangan:
* **CAPEX (*Capital Expenditure*):** Biaya modal yang dikeluarkan di muka dalam jumlah besar untuk membeli aset fisik jangka panjang (server, storage SAN, switch jaringan, genset, AC data center).
* **OPEX (*Operational Expenditure*):** Biaya operasional rutin yang dikeluarkan saat sistem berjalan (tagihan listrik, internet, gaji admin, lisensi langganan bulanan, atau biaya sewa public cloud).

### Arus Kas vs Depresiasi Akuntansi
Beli perangkat keras server tidak langsung dicatat sebagai kerugian di bulan pertama, melainkan disusutkan secara bertahap:
$$\text{Depresiasi Garis Lurus per Tahun} = \frac{\text{Harga Pembelian Aset}}{\text{Estimasi Umur Manfaat}}$$
*Contoh:* Membeli server seharga Rp600 juta untuk masa pakai 5 tahun berarti ada beban akuntansi depresiasi sebesar **Rp120 juta per tahun**. Namun secara **arus kas (*cash flow*)**, uang Rp600 juta tunai sudah harus keluar di muka saat pembelian dilakukan.

---

## 2. Perbandingan Karakteristik Finansial

| Sisi Penilaian | Private Cloud (Berbasis CAPEX) | Public Cloud (Berbasis OPEX) |
| :--- | :--- | :--- |
| **Arus Kas** | Berat di awal (*upfront cost* besar). | Tersebar tiap bulan sesuai pemakaian. |
| **Kapasitas** | Harus dibeli dan diestimasi di muka. | Fleksibel; bisa ditambah atau dikurangi kapan saja. |
| **Risiko Utilisasi** | Ditanggung sendiri jika server menganggur. | Dialihkan ke provider. |
| **Tingkat Kendali** | Kendali fisik dan konfigurasi penuh. | Mengikuti aturan dan katalog penyedia. |
| **Tantangan Biaya** | Risiko beli kapasitas berlebih (*overprovisioning*). | Risiko tagihan membengkak jika konsumsi boros. |

---

## 3. Menghitung Total Cost of Ownership (TCO)
TCO adalah total seluruh biaya yang dikeluarkan sepanjang siklus hidup sistem, bukan cuma harga beli barang di faktur:
$$\text{TCO} = \text{Biaya Investasi Awal} + \text{Biaya Operasional Rutin} + \text{Biaya Risiko \& Akhir Masa Pakai}$$

Komponen TCO yang sering terlewat:
* **Biaya Orang (SDM):** Biaya gaji teknisi, sertifikasi, dan jam kerja lembur.
* **Kapasitas Menganggur (*Idle*):** Server yang dibeli mahal tapi pemakaiannya hanya 15%.
* **Biaya Risiko:** Kerugian finansial saat sistem down atau insiden kehilangan data.
* **Biaya Pengalihan (*Exit Cost*):** Biaya transfer data keluar jika suatu saat ingin pindah provider.

---

## 4. Konsep Unit Economics & Dilema Utilisasi
Daripada hanya melihat total biaya miliaran, bisnis lebih mudah menilai efisiensi lewat **Unit Economics**:
* Biaya per VM per bulan
* Biaya infrastruktur per transaksi pelanggan
* Biaya sistem per mahasiswa/pengguna aktif

### Mengapa Utilisasi 100% Bukan Hal yang Bagus?
* **Utilisasi terlalu rendah (< 30%):** Banyak kapasitas menganggur, biaya per unit jadi sangat mahal.
* **Utilisasi ideal (70% - 80%):** Efisien secara biaya, tapi masih memiliki sisa ruang aman (**headroom**) untuk mengantisipasi lonjakan mendadak dan kegagalan komponen.
* Jika utilisasi dipaksa mendekati 100%, sistem akan langsung lambat (*lag*) begitu ada sedikit kenaikan trafik.

---

## 5. Studi Kasus: Private Cloud vs Public Cloud untuk Kampus

### Data Kebutuhan Kampus (Analisis 5 Tahun):
* Kebutuhan: 120 VM ekuivalen, 80 TB Storage, Target ketersediaan 99,9%.
* **Opsi A (Private Cloud On-Premise):**
  * CAPEX awal (server, storage, implementasi): Rp1,2 Miliar
  * OPEX tahunan (daya, maintenance, support): Rp300 Juta / tahun
  * $\text{Total Biaya 5 Tahun} = \text{Rp}1,2\text{ M} + (5 \times \text{Rp}0,3\text{ M}) = \mathbf{Rp2,7\text{ Miliar}}$
* **Opsi B (Public Cloud):**
  * Biaya migrasi awal: Rp100 Juta
  * Biaya sewa cloud tahunan: Rp520 Juta / tahun
  * $\text{Total Biaya 5 Tahun} = \text{Rp}0,1\text{ M} + (5 \times \text{Rp}0,52\text{ M}) = \mathbf{Rp2,7\text{ Miliar}}$

### Analisis Kritis: Nominalnya Sama-Sama Rp2,7 Miliar, Lalu Pilih yang Mana?
Karena biaya akhirnya persis sama, keputusan harus dilihat dari faktor strategis lainnya:
1. **Ketersediaan Dana Tunai:** Apakah kampus memiliki dana kas segar Rp1,2 Miliar langsung di awal? Jika tidak, mencicil lewat public cloud (Rp520 juta/tahun) jauh lebih aman bagi likuiditas keuangan.
2. **Kesiapan Staf TI:** Apakah kampus punya tim sysadmin/DevOps yang sanggup merawat server fisik 24 jam sehari? Jika tim terbatas, opsi public cloud mengurangi beban operasional hardware.
3. **Pola Beban Kampus:** Beban kampus sifatnya musiman (sangat tinggi saat KRS/awal semester, lalu lengang saat libur semester). Pada public cloud, saat libur semester kapasitas bisa diturunkan agar tagihan mengecil.
4. **Analisis Sensitivitas:** Jika pemakaian data membengkak atau nilai tukar dolar naik drastis, biaya public cloud bisa melonjak melewati Rp2,7 Miliar.

---

## 6. Risiko Biaya yang Kerap Diabaikan
* **Technical Debt:** Menghemat biaya di awal dengan membeli hardware murah/lama sering kali menimbulkan biaya perbaikan yang jauh lebih mahal di kemudian hari.
* **Skill & Staffing:** Kesulitan mencari atau mempertahankan staf yang kompeten mengelola private cloud.
* **Vendor Lock-in:** Terlalu bergantung pada fitur khusus satu provider sehingga biaya migrasi keluar menjadi sangat mahal.
* **Governance Lemah:** Server uji coba lupa dimatikan sehingga tagihan cloud terus berjalan tanpa ada yang merasa memiliki.
