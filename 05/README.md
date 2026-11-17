Materi Minggu 5: Metode Kuantitatif Ekonomi Infrastruktur untuk Deployment Cloud
Prompt: "Rangkum materi metode kuantitatif ekonomi cloud, rumus metrik TCO, ROI, dan Payback Period, serta simulasi perbandingan biaya 3 tahun antara Private Cloud vs Public Cloud berdasarkan data slide pertemuan 5."
Bagian yang disesuaikan dari keluaran prompt ada pada: Menyajikan langkah perhitungan matematika secara berurutan dan runtut agar mudah diikuti, menyederhanakan definisi konsep finansial ke bahasa sehari-hari, serta merangkum praktik FinOps yang relevan untuk mengendalikan biaya.

---

# Catatan Kuliah: Metode Kuantitatif Ekonomi Infrastruktur Cloud

## 1. Mengapa Analisis Kuantitatif Diperlukan?
Memilih antara membeli server sendiri (Private Cloud) atau menyewa layanan (Public Cloud) tidak boleh sekadar menebak atau ikut-ikutan tren. Keputusan harus didukung oleh angka dan analisis kuantitatif untuk melihat:
* Berapa total biaya riil sepanjang masa pakai?
* Berapa manfaat finansial yang didapatkan?
* Berapa lama modal awal investasi bisa balik (*break-even*)?

---

## 2. Enam Komponen Biaya Infrastruktur
Bukan cuma harga hardware atau biaya sewa bulanan, ada 6 komponen biaya yang harus diperhitungkan:
1. **CAPEX:** Pembelian awal server, rak, storage, dan switch jaringan.
2. **OPEX:** Tagihan listrik harian, pendingin ruangan, sewa koneksi internet, dan lisensi software.
3. **People Cost:** Gaji tim sysadmin, network engineer, database administrator, dan biaya training staf.
4. **Transition Cost:** Biaya migrasi data awal, penyesuaian aplikasi, dan masa uji coba sistem paralel.
5. **Risk Cost:** Kerugian finansial yang timbul saat sistem mati (*downtime*) atau insiden keamanan.
6. **Exit Cost (Biaya Pengalihan):** Biaya pemindahan data dan biaya transfer keluar (*data egress fee*) jika memutuskan berhenti berlangganan.

---

## 3. Rumus Metrik Finansial Sederhana

* **TCO (*Total Cost of Ownership*):**
  $$\text{TCO} = \text{Biaya Awal} + \text{Biaya Operasi Kumulatif} + \text{Biaya Transisi} + \text{Biaya Risiko \& Keluar}$$
* **ROI Sederhana (*Return on Investment*):**
  Mengukur persentase keuntungan relatif terhadap total biaya yang dikeluarkan:
  $$\text{ROI} = \frac{\text{Total Manfaat} - \text{Total Biaya (TCO)}}{\text{Total Biaya (TCO)}} \times 100\%$$
* **Payback Period:**
  Waktu yang diperlukan agar manfaat bersih tahunan bisa menutup biaya investasi awal:
  $$\text{Payback Period} = \frac{\text{Biaya Investasi \& Transisi di Awal}}{\text{Manfaat Bersih Tahunan}}$$

---

## 4. Simulasi Studi Kasus 3 Tahun: Private vs Public Cloud

### Skenario Kasus:
Sebuah perusahaan menjalankan aplikasi ERP dan portal internal selama **3 tahun**, dengan estimasi manfaat efisiensi bisnis sebesar **Rp1.200 Juta / tahun** (Total Manfaat 3 Tahun = **Rp3.600 Juta**).

### Data Input Biaya (Juta Rupiah):
| Komponen Biaya | Private Cloud | Public Cloud |
| :--- | :---: | :---: |
| Investasi Awal | Rp1.200 jt | Rp100 jt |
| Operasi Infrastruktur / Tahun | Rp300 jt | Rp480 jt |
| Tenaga Ahli / Tahun | Rp250 jt | Rp150 jt |
| Migrasi & Transisi (1x di awal) | Rp150 jt | Rp200 jt |
| Biaya Keluar / Egress di Akhir | Rp0 jt | Rp80 jt |

---

### Perhitungan Langkah Demi Langkah:

#### 1. Perhitungan TCO 3 Tahun
* **Private Cloud:**
  $$\text{TCO} = 1.200 + (300 \times 3) + (250 \times 3) + 150 = 1.200 + 900 + 750 + 150 = \mathbf{Rp3.000\text{ Juta}}$$
* **Public Cloud:**
  $$\text{TCO} = 100 + (480 \times 3) + (150 \times 3) + 200 + 80 = 100 + 1.440 + 450 + 200 + 80 = \mathbf{Rp2.270\text{ Juta}}$$
* *Kesimpulan TCO:* Public cloud lebih murah **Rp730 Juta (sekitar 24,3%)** dibanding private cloud pada asumsi dasar ini.

#### 2. Perhitungan ROI Sederhana
* **Private Cloud:**
  $$\text{ROI} = \frac{3.600 - 3.000}{3.000} \times 100\% = \frac{600}{3.000} \times 100\% = \mathbf{20,0\%}$$
* **Public Cloud:**
  $$\text{ROI} = \frac{3.600 - 2.270}{2.270} \times 100\% = \frac{1.330}{2.270} \times 100\% \approx \mathbf{58,6\%}$$

#### 3. Perhitungan Payback Period
* **Private Cloud:**
  * Modal Awal $= 1.200 + 150 = \text{Rp}1.350\text{ Juta}$
  * Manfaat Bersih per Tahun $= 1.200 - (300 + 250) = \text{Rp}650\text{ Juta/tahun}$
  * $\text{Payback Period} = \frac{1.350}{650} \approx \mathbf{2,08\text{ Tahun}}$
* **Public Cloud:**
  * Modal Awal $= 100 + 200 = \text{Rp}300\text{ Juta}$
  * Manfaat Bersih per Tahun $= 1.200 - (480 + 150) = \text{Rp}570\text{ Juta/tahun}$
  * $\text{Payback Period} = \frac{300}{570} \approx \mathbf{0,53\text{ Tahun (sekitar 6,4 bulan)}}$

---

## 5. Uji Sensitivitas: Bagaimana Jika Biaya Public Cloud Melonjak?
Perhitungan di atas mengasumsikan kondisi stabil. Namun, bagaimana jika biaya operasional public cloud ternyata membengkak **30%** (misalnya akibat lonjakan pemakaian data dan kenaikan kurs dolar)?
* Biaya operasional public naik dari Rp480 jt menjadi Rp624 jt/tahun (+Rp144 jt/tahun).
* Tambahan biaya 3 tahun $= 3 \times \text{Rp}144\text{ jt} = \text{Rp}432\text{ jt}$.
* $\text{TCO Public Baru} = 2.270 + 432 = \mathbf{Rp2.702\text{ Juta}}$.
* *Dampak:* Keunggulan penghematan public cloud menyusut dari Rp730 jt menjadi hanya Rp298 jt. Hal ini membuktikan pentingnya pengujian batas risiko sebelum mengambil keputusan.

---

## 6. Pengendalian Biaya dengan FinOps
Agar biaya cloud tidak bocor tak terkontrol, perusahaan perlu menerapkan praktik FinOps:
* **Tagging:** Memberi label jelas pada setiap mesin server virtual (milik departemen mana dan untuk keperluan apa).
* **Right-sizing:** Memilih kapasitas CPU dan RAM sesuai beban kerja riil, bukan memilih paket terbesar "untuk jaga-jaga".
* **Scheduling:** Mengatur server pengujian agar otomatis mati di malam hari atau saat akhir pekan.
* **Reserved Capacity:** Mengikat kontrak komitmen 1-3 tahun untuk server yang sudah pasti dipakai terus demi mendapatkan diskon besar dari penyedia cloud.
