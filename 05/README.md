# Rangkuman Perkuliahan Business Cloud Design

**Materi Minggu 5: Metode Kuantitatif Ekonomi Infrastruktur untuk Deployment Cloud**  
**Prompt:**  
> "Tolong buatkan rangkuman komprehensif untuk materi kuliah Business Cloud Design Pertemuan 5 dengan topik 'Metode Kuantitatif Ekonomi Infrastruktur untuk Deployment Cloud'. Rangkuman harus mencakup: peran metode kuantitatif dalam keputusan teknologi, pemetaan 6 komponen biaya infrastruktur (CAPEX, OPEX, People cost, Transition cost, Risk cost, Exit/Egress cost), formula metrik finansial utama (TCO, ROI sederhana, Payback Period, NPV), simulasi studi kasus perbandingan 3 tahun antara Private Cloud vs Public Cloud beserta rincian kalkulasi matematika langkah demi langkah (TCO, ROI, Payback), analisis sensitivitas terhadap fluktuasi biaya dan risiko, serta strategi tata kelola FinOps untuk mencegah pembengkakan biaya komputasi."

**Bagian yang disesuaikan dari keluaran prompt ada pada:**  
1. Menyusun tabel simulasi komparasi finansial 3 tahun secara sistematis dengan rincian rumus perhitungan yang transparan dan mudah diverifikasi.  
2. Mengelaborasi rumus *Payback Period* dengan membedakan investasi kas di muka (*upfront capital*) terhadap aliran manfaat kas bersih tahunan (*annual net cash flow*).  
3. Memperdalam penjelasan mengenai *Exit Cost* dan *Data Egress Fee* yang kerap menjadi biaya jebakan pada arsitektur public cloud.  
4. Memaparkan praktik implementasi FinOps operasional (seperti *tagging*, *rightsizing*, *scheduling*, dan instans reservasi).

---

## 1. Peran Metode Kuantitatif dalam Pengambilan Keputusan Cloud
Keputusan pemilihan arsitektur cloud (*Private*, *Public*, atau *Hybrid*) tidak boleh didasarkan pada preferensi subjektif atau tren teknologi semata. Analisis kuantitatif objektif diperlukan untuk:
* Mengukur kelayakan finansial jangka panjang.
* Menghubungkan investasi teknologi dengan nilai tambah bisnis (*business value*).
* Mengidentifikasi ambang batas risiko biaya operasional di masa depan.

---

## 2. Peta 6 Komponen Biaya Infrastruktur
Banyak organisasi melakukan kesalahan fatal dengan hanya membandingkan biaya sewa server atau harga pembelian hardware. Biaya komprehensif terdiri atas:
1. **CAPEX (Biaya Modal):** Server fisik, storage array (SAN/NAS), perangkat jaringan, rak server, UPS, fasilitas fisik data center, dan biaya instalasi awal.
2. **OPEX (Biaya Operasional):** Tagihan listrik, sistem pendingin (HVAC), sewa konektivitas internet/leased line, lisensi software, biaya pemeliharaan vendor, dan tagihan komputasi cloud.
3. **People Cost (Biaya Personel):** Gaji, tunjangan, dan insentif untuk administrator sistem, teknisi jaringan, database administrator (DBA), spesialis keamanan siber, dan biaya pelatihan berkala.
4. **Transition Cost (Biaya Transisi):** Biaya *assessment* awal, rekayasa arsitektur migrasi, pengujian integrasi sistem, dan biaya *parallel run* selama masa transisi.
5. **Risk Cost (Biaya Risiko):** Estimasi kerugian finansial akibat potensi *downtime*, insiden kebocoran data, denda kepatuhan hukum, dan biaya *over-provisioning*.
6. **Exit Cost / Egress Fee (Biaya Terminasi & Pengalihan):** Biaya pemindahan kembali data ke lokal atau vendor lain, penalti pemutusan kontrak lebih awal, serta biaya transfer data keluar (*data egress fee*) yang dihitung per gigabyte oleh provider public cloud.

---

## 3. Formula Metrik Finansial Utama
* **Total Cost of Ownership (TCO):**
  $$\text{TCO} = \text{Biaya Awal} + \sum \text{Biaya Operasional} + \text{Biaya Transisi} + \text{Biaya Risiko \& Terminasi}$$
* **Return on Investment (ROI Sederhana):**
  $$\text{ROI} (\%) = \frac{\text{Total Manfaat Finansial} - \text{Total Biaya (TCO)}}{\text{Total Biaya (TCO)}} \times 100\%$$
* **Payback Period (Periode Balik Modal):**
  $$\text{Payback Period} = \frac{\text{Investasi \& Transisi Awal}}{\text{Manfaat Bersih Tahunan (Manfaat Tahunan} - \text{OPEX Tahunan)}}$$
* **Net Present Value (NPV):** Menghitung nilai sekarang dari seluruh arus kas masuk dan keluar di masa depan dengan memperhitungkan faktor diskonto suku bunga dan inflasi (*time value of money*).

---

## 4. Simulasi Studi Kasus 3 Tahun: Private Cloud vs Public Cloud

### Parameter Kasus:
* Organisasi mengoperasikan sistem ERP, portal pelanggan, dan analitik data internal selama horizon **3 tahun**.
* Manfaat finansial terukur yang dihasilkan: **Rp1.200 Juta / tahun** (Total Manfaat 3 Tahun = **Rp3.600 Juta**).

### Tabel Input Biaya (Satuan: Juta Rupiah)
| Komponen Biaya | Private Cloud | Public Cloud |
| :--- | :---: | :---: |
| **Investasi Awal (CAPEX)** | Rp1.200 jt | Rp100 jt |
| **Operasi Infrastruktur / Tahun** | Rp300 jt | Rp480 jt |
| **Tenaga Ahli (People) / Tahun** | Rp250 jt | Rp150 jt |
| **Migrasi & Transisi (Satu Kali)** | Rp150 jt | Rp200 jt |
| **Biaya Keluar / Egress di Akhir Horizon** | Rp0 jt | Rp80 jt |

---

### Kalkulasi Matematika Langkah Demi Langkah:

#### A. Total Cost of Ownership (TCO) 3 Tahun
* **Private Cloud:**
  $$\text{TCO}_{\text{Private}} = 1.200 + (300 \times 3) + (250 \times 3) + 150 = 1.200 + 900 + 750 + 150 = \mathbf{Rp3.000\text{ Juta}}$$
* **Public Cloud:**
  $$\text{TCO}_{\text{Public}} = 100 + (480 \times 3) + (150 \times 3) + 200 + 80 = 100 + 1.440 + 450 + 200 + 80 = \mathbf{Rp2.270\text{ Juta}}$$
* **Selisih Awal:** Public Cloud lebih hemat **Rp730 Juta (sekitar 24,3%)** dibanding Private Cloud pada asumsi dasar.

#### B. Return on Investment (ROI Sederhana)
* **Private Cloud:**
  $$\text{ROI}_{\text{Private}} = \frac{3.600 - 3.000}{3.000} \times 100\% = \frac{600}{3.000} \times 100\% = \mathbf{20,0\%}$$
* **Public Cloud:**
  $$\text{ROI}_{\text{Public}} = \frac{3.600 - 2.270}{2.270} \times 100\% = \frac{1.330}{2.270} \times 100\% \approx \mathbf{58,6\%}$$

#### C. Payback Period (Waktu Balik Modal)
* **Private Cloud:**
  * Investasi Awal + Transisi $= 1.200 + 150 = \text{Rp}1.350\text{ Juta}$
  * Manfaat Bersih Tahunan $= 1.200 - (300 + 250) = \text{Rp}650\text{ Juta/tahun}$
  * $\text{Payback}_{\text{Private}} = \frac{1.350}{650} \approx \mathbf{2,08\text{ Tahun}}$
* **Public Cloud:**
  * Investasi Awal + Transisi $= 100 + 200 = \text{Rp}300\text{ Juta}$
  * Manfaat Bersih Tahunan $= 1.200 - (480 + 150) = \text{Rp}570\text{ Juta/tahun}$
  * $\text{Payback}_{\text{Public}} = \frac{300}{570} \approx \mathbf{0,53\text{ Tahun (sekitar 6,4 bulan)}}$

---

## 5. Analisis Sensitivitas & Pengujian Asumsi Kritis
Keputusan tidak boleh berhenti pada satu angka statis. Analisis sensitivitas menguji perubahan variabel paling berpengaruh:
* **Uji Kasus Kenaikan Biaya Public Cloud sebesar 30%:**
  * Biaya operasional tahunan naik dari Rp480 jt menjadi Rp624 jt/tahun (+Rp144 jt/tahun).
  * Kenaikan biaya 3 tahun $= 3 \times \text{Rp}144\text{ jt} = \text{Rp}432\text{ jt}$.
  * $\text{TCO Public Baru} = 2.270 + 432 = \mathbf{Rp2.702\text{ Juta}}$.
  * Selisih efisiensi terhadap Private Cloud terpangkas drastis dari Rp730 jt menjadi hanya Rp298 jt.
* **Variabel Kritis Lain yang Wajib Diuji:**
  * Tingkat pertumbuhan volume transfer data keluar (*data egress rate*).
  * Kebutuhan akselerator grafis kustom (GPU AI).
  * Fluktuasi kurs mata uang asing (USD ke IDR).
  * Utilisasi nyata kapasitas server pada private cloud.

---

## 6. Tata Kelola FinOps untuk Pengendalian Biaya
Untuk menjaga efisiensi biaya secara berkesinambungan, organisasi wajib menerapkan praktik FinOps:
1. **Resource Tagging & Ownership:** Mewajibkan penandaan (*tag*) pemilik, departemen, dan *cost center* pada setiap instans cloud.
2. **Rightsizing:** Menyesuaikan alokasi vCPU, memori RAM, dan kapasitas IOPS secara rutin berdasarkan pola penggunaan nyata (*historical metrics*).
3. **Automated Scheduling:** Mematikan mesin instans lingkungan pengujian (*development/staging*) di luar jam kerja secara otomatis.
4. **Reserved Instances / Savings Plans:** Memanfaatkan komitmen penggunaan jangka panjang (1-3 tahun) untuk mendapatkan diskon hingga 40-70% pada beban kerja stabil.
