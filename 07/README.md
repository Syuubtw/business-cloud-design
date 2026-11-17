Materi Minggu 7: Skalabilitas Berbasis Kontainer & Virtualisasi
Prompt: "Rangkum materi Skalabilitas Berbasis Kontainer dan Virtualisasi, jelaskan perbandingan Scale-up vs Scale-out, perbedaan VM vs Kontainer, peran Kubernetes, arsitektur hibrida VM+Kontainer, dan dampak penghematan FinOps."
Bagian yang disesuaikan dari keluaran prompt ada pada: Mengurangi gaya bahasa pemasaran cloud yang berlebihan, merapikan tabel perbandingan VM dan Docker agar lebih to the point, serta menguraikan penghematan FinOps (hemat hardware 60%, lisensi 80%) secara jelas dan mudah dipahami.

---

# Catatan Kuliah: Skalabilitas Berbasis Kontainer & Virtualisasi

## 1. Menghadapi Lonjakan Beban: Scale-Up vs Scale-Out
Saat jumlah pengguna aplikasi melonjak tajam, ada dua pendekatan untuk meningkatkan kapasitas sistem:

* **Scale-Up (Vertical Scaling):**
  * Menambah spesifikasi hardware pada server yang sama (tambah vCPU, tambah RAM, perbesar disk).
  * *Kelemahan:* Ada batas fisik maksimal hardware (*hardware ceiling*) dan biasanya server harus dimatikan (*restart/downtime*) saat upgrade dilakukan.
* **Scale-Out (Horizontal Scaling):**
  * Menambah jumlah unit server atau kontainer secara paralel yang bekerja bersama-sama.
  * *Kelebihan:* Skalabilitas praktis tanpa batas (*virtually unlimited*), tidak ada gangguan layanan (*zero downtime*), dan beban dibagi rata oleh load balancer. Sangat cocok untuk arsitektur aplikasi modern (*cloud-native*).

---

## 2. Mengenal Arsitektur Virtual Machine (VM)
Virtual Machine membagi satu server fisik menjadi beberapa komputer virtual terisolasi menggunakan software bernama **Hypervisor**:
* **Hypervisor Type 1 (Bare-Metal):** Berjalan langsung di atas perangkat keras fisik tanpa sistem operasi perantara (contoh: VMware ESXi, KVM). Ini standar yang dipakai di data center enterprise.
* **Hypervisor Type 2 (Hosted):** Berjalan sebagai program aplikasi di atas OS utama laptop/komputer kita (contoh: VirtualBox, VMware Workstation).
* Setiap VM menjalankan **Guest OS sendiri secara lengkap**, sehingga membutuhkan alokasi memori RAM dan ruang penyimpanan disk yang cukup besar (beberapa Gigabyte per VM).

---

## 3. Arsitektur Kontainer (Docker & containerd)
Berbeda dengan VM, kontainer tidak membawa sistem operasi lengkap di dalamnya. Kontainer hanya mengemas kode aplikasi beserta pustaka (*libraries*) yang dibutuhkannya, lalu **berbagi kernel dengan sistem operasi host** (*kernel sharing*).

### Mengapa Kontainer Sangat Populer?
1. **Booting Super Cepat:** Aplikasi kontainer bisa menyala dalam hitungan **detik atau milidetik**, karena tidak perlu melalui proses booting OS dari awal.
2. **Ukuran File Sangat Ringan:** Hanya berukuran puluhan hingga ratusan Megabyte (MB), jauh lebih kecil dibanding image VM yang berukuran Gigabyte (GB).
3. **Konsistensi Lingkungan:** Mengeliminasi masalah klasik programmer *"di laptop saya jalan, tapi di server error"* karena semua dependensi terbungkus rapi di dalam image.
4. **Hemat Memori:** Membutuhkan konsumsi RAM 30% sampai 50% lebih sedikit dibanding VM.

---

## 4. Tabel Perbandingan Ringkas: VM vs Kontainer

| Karakteristik | Virtual Machine (VM) | Kontainer (Docker) |
| :--- | :--- | :--- |
| **Lapisan Abstraksi** | Tingkat Hardware (lewat Hypervisor) | Tingkat Sistem Operasi (berbagi Kernel Host) |
| **Waktu Booting** | 2 sampai 5 Menit | Hitungan Detik (< 1 - 3 Detik) |
| **Ukuran Image** | Besar (beberapa GB) | Sangat Ringan (puluhan/ratusan MB) |
| **Isolasi Keamanan** | Sangat Keras (Hardware-level) | Isolasi Proses (*Process-level*) |
| **Kecepatan Penskalaan** | Relatif lambat dan berat | Sangat cepat dan fleksibel |

> **Dampak ke Bisnis:** Kecepatan autoscaling kontainer yang mampu bereaksi dalam waktu **< 3 detik** melindungi bisnis dari kerugian finansial akibat server tumbang saat terjadi serbuan transaksi mendadak.

---

## 5. Orkestrasi dengan Kubernetes (K8s)
Jika kita menjalankan ratusan kontainer di server produksi, mustahil mengelolanya satu per satu secara manual. Di sinilah peran **Kubernetes**:
* **Auto-Scaling (HPA):** Menambah atau mengurangi jumlah pod kontainer secara otomatis saat beban pemakaian CPU/RAM melonjak.
* **Self-Healing:** Jika ada kontainer yang error, macet, atau mati mendadak, Kubernetes akan langsung mendeteksinya dan membuat kontainer baru sebagai pengganti.
* **Load Balancing:** Membagi trafik pengguna secara merata ke seluruh kontainer yang aktif dan sehat.

---

## 6. Arsitektur Standar Industri: Gabungan VM + Kontainer
Di dunia kerja nyata, arsitektur yang umum diterapkan adalah menggabungkan keduanya:
* **VM sebagai Fondasi Infrastruktur:** Dipakai untuk menyewa node komputasi di cloud provider (seperti AWS EC2) demi jaminan keamanan dan isolasi keras antar-akun.
* **Kontainer di Dalam VM:** Aplikasi dan mikroservis dijalankan di dalam kontainer di atas VM tersebut demi kecepatan deployment, kemudahan update, dan efisiensi memori.

---

## 7. Dampak FinOps & Penghematan Biaya (TCO)
Beralih dari arsitektur VM murni ke kontainer memberikan efisiensi biaya yang sangat masif:
* **Hemat Hardware (CAPEX):** Beban kerja yang biasanya butuh $\pm$ 10 server fisik berbasis VM bisa dirampingkan menjadi hanya $\pm$ 4 server fisik berbasis kontainer (*hemat biaya hardware hingga 60%*).
* **Hemat Lisensi:** Memangkas biaya pembelian lisensi sistem operasi Windows Server atau lisensi hypervisor berbayar hingga 80%.
* **Hemat Listrik & Pendingin (OPEX):** Berkurangnya jumlah server fisik di rak data center memotong tagihan listrik dan AC pendingin hingga 60%.
* **Optimasi Utilisasi:** Tingkat utilisasi CPU dan RAM bisa dimaksimalkan mencapai 75% - 80% tanpa membiarkan mesin menganggur.

---

## 8. Studi Kasus Nyata
* **E-Commerce Flash Sale:** Menghadapi lonjakan pembeli 10x lipat dalam waktu singkat. Dengan Kubernetes HPA, ribuan pod kontainer aplikasi katalog diperbanyak otomatis dalam tempo 30 detik tanpa mengganggu sistem pembayaran.
* **Sistem Perbankan Digital:** Menggabungkan isolasi ketat VM untuk menyimpan database transaksi finansial nasabah, sedangkan aplikasi mobile banking dijalankan di atas kontainer agar tim pengembang bisa sering merilis fitur baru dengan cepat dan aman.
