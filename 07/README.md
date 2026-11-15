# Rangkuman Perkuliahan Business Cloud Design

**Materi Minggu 7: Skalabilitas Berbasis Kontainer & Virtualisasi**  
**Prompt:**  
> "Tolong buatkan rangkuman komprehensif untuk materi kuliah Business Cloud Design Pertemuan 7 dengan topik 'Skalabilitas Berbasis Kontainer & Virtualisasi: Arsitektur Efisiensi Sumber Daya, Elastisitas Beban Kerja, dan Strategi Deployment Cloud Modern'. Rangkuman harus mencakup: dimensi penskalaan sistem (Scale-up/Vertical vs Scale-out/Horizontal), arsitektur Virtual Machine (Hypervisor Type 1 vs Type 2, PVM vs HVM), arsitektur kontainer modern (kernel sharing, Docker/containerd), perbandingan komprehensif VM vs Kontainer pada 5 metrik evaluasi, dampak kinerja bisnis berupa elastisitas waktu nyata (< 3 detik), kapabilitas orkestrasi Kubernetes (HPA, self-healing, load balancing), arsitektur standar produksi hibrida (VM + Kontainer), analisis efisiensi FinOps & kalkulasi penghematan TCO (hardware, lisensi, daya listrik/HVAC), serta implementasi pada studi kasus e-commerce flash sale dan perbankan digital."

**Bagian yang disesuaikan dari keluaran prompt ada pada:**  
1. Menyusun tabel komparasi teknis komprehensif antara Virtual Machine (VM) dan Kontainer (Docker) yang merinci tingkat abstraksi, waktu booting, ukuran artefak, isolasi keamanan, dan kecepatan penskalaan.  
2. Mengelaborasi arsitektur hibrida standar industri di mana klaster kontainer Kubernetes dijalankan di atas node VM untuk menggabungkan isolasi multi-tenant dengan portabilitas mikroservis.  
3. Memperinci analisis kuantitatif FinOps yang memperlihatkan penghematan CAPEX hingga 60% dan pemangkasan lisensi OS/hypervisor hingga 80% melalui konsolidasi densitas kontainer.  
4. Memaparkan implementasi dua studi kasus nyata: penanganan lonjakan trafik 10x pada *E-commerce Flash Sale* dan arsitektur keamanan bertingkat pada *Sistem Perbankan Digital*.

---

## 1. Dimensi Penskalaan Sistem: Scale-Up vs Scale-Out
Dalam merancang arsitektur cloud untuk menghadapi fluktuasi beban bisnis, terdapat dua pendekatan mendasar:

| Karakteristik | Scale-Up (Vertical Scaling) | Scale-Out (Horizontal Scaling) |
| :--- | :--- | :--- |
| **Mekanisme** | Menambahkan kapasitas (vCPU, RAM, Disk) ke satu server fisik/VM yang ada. | Menambahkan jumlah instans/node server paralel secara elastis. |
| **Batas Maksimum** | Dibatasi oleh batas fisik spesifikasi perangkat keras server (*hardware ceiling*). | Secara teoritis tidak terbatas (*virtually unlimited*), mengikuti kebutuhan trafik. |
| **Resiko Downtime** | Sering membutuhkan *restart* atau *interrupted service* saat konfigurasi diubah. | Tidak ada gangguan layanan (*zero downtime*); beban dialihkan dinamis. |
| **Kesesuaian Beban** | Cocok untuk basis data monolitik tradisional dengan ketergantungan relasional ketat. | Standar emas untuk arsitektur *microservices*, *stateless apps*, dan sistem cloud-native. |

---

## 2. Arsitektur Virtual Machine (VM)
Virtual Machine membagi sumber daya perangkat keras fisik menjadi beberapa sistem operasi tamu (*Guest OS*) independen melalui lapisan **Hypervisor**:
* **Hypervisor Type 1 (Bare-Metal):** Berjalan langsung di atas perangkat keras fisik tanpa OS perantara (contoh: VMware ESXi, KVM, Xen). Menawarkan performa tinggi dan efisiensi tingkat perusahaan.
* **Hypervisor Type 2 (Hosted):** Berjalan sebagai aplikasi di atas Sistem Operasi Host (contoh: Oracle VirtualBox, VMware Workstation). Umumnya digunakan untuk pengujian lokal di laptop pengembang.
* **Mekanisme Virtualisasi:**
  * *Paravirtualization (PVM):* Kernel sistem operasi tamu dimodifikasi agar menyadari bahwa ia berjalan di atas hypervisor, sehingga panggilan sistem (*hypercalls*) dilakukan secara efisien.
  * *Hardware-Assisted Virtualization (HVM):* Memanfaatkan fitur ekstensi virtualisasi langsung dari prosesor CPU fisik (Intel VT-x atau AMD-V) tanpa perlu memodifikasi kernel OS tamu.

---

## 3. Arsitektur Kontainer Modern
Berbeda dengan VM, kontainer tidak mengemas sistem operasi lengkap. Kontainer mengisolasi proses aplikasi pada tingkat sistem operasi dengan **berbagi kernel dari Host OS** (*kernel sharing*) menggunakan fitur bawaan Linux (*cgroups* dan *namespaces*).
* **Container Engine:** Perangkat lunak yang bertugas membangun, menjalankan, dan mendistribusikan *container image* (contoh: Docker, containerd, CRI-O).
* **Karakteristik Unggulan Kontainer:**
  1. *Startup dalam Hitungan Detik/Milidetik:* Proses inisialisasi instan karena tidak melalui siklus *booting* OS dan inisialisasi driver hardware.
  2. *Paket Konsisten:* Menjamin tidak adanya masalah *"it works on my machine"* karena seluruh kode sumber, runtime, pustaka, dan konfigurasi dikemas identik.
  3. *Efisiensi Memori Tinggi:* Menghemat penggunaan memori RAM 30% hingga 50% lebih efisien dibanding VM konvensional.

---

## 4. Analisis Komparatif: VM vs Kontainer

| Metrik Evaluasi | Virtual Machine (VM) | Kontainer (Docker) |
| :--- | :--- | :--- |
| **Tingkat Abstraksi** | Tingkat Perangkat Keras (*Hypervisor-level*) | Tingkat Sistem Operasi (*Kernel Sharing*) |
| **Waktu Booting** | Menit (2 – 5 Menit) | Detik hingga Milidetik (< 1 – 3 Detik) |
| **Ukuran Image** | Besar (Beberapa Gigabyte / GB) | Sangat Ringan (Megabyte / MB) |
| **Isolasi & Keamanan** | Isolasi Keras (*Hardware Level Isolation*) | Isolasi Proses (*Process Level Isolation*) |
| **Kecepatan Skalabilitas** | Relatif lambat dan berat | Sangat cepat, elastis, dan dinamis |

> **Dampak Kinerja Bisnis:** Elastisitas kontainer yang mampu melakukan *auto-scaling* dalam waktu **< 3 detik** melindungi bisnis dari kerugian finansial akibat *system outage* saat lonjakan transaksi tiba-tiba.

---

## 5. Orkestrasi dengan Kubernetes (K8s)
Dalam ekosistem produksi berskala besar dengan ratusan kontainer, diperlukan sistem orkestrasi otomatis seperti **Kubernetes**:
* **Horizontal Pod Autoscaler (HPA):** Menambah atau mengurangi jumlah replika *pod* aplikasi secara otomatis berdasarkan metrik konsumsi CPU, memori, atau metrik bisnis kustom.
* **Self-Healing System:** Memantau kesehatan kontainer secara *real-time*. Jika ada kontainer yang *crash* atau *unresponsive*, Kubernetes secara otomatis mematikannya dan membuat instans baru pengganti (*auto-restart & replace*).
* **Service Discovery & Load Balancing:** Mendistribusikan trafik jaringan secara merata ke seluruh pod yang sehat tanpa intervensi manual.

---

## 6. Arsitektur Hibrida Produksi: VM + Kontainer
Di lingkungan komersial perusahaan (*enterprise cloud*), VM dan Kontainer tidak saling menggantikan, melainkan dikombinasikan secara sinergis:

```
[ Lapisan Aplikasi / Microservices ] -> Berjalan di dalam Kontainer (Docker/K8s)
                                       (Fleksibel, portabel, rilis cepat, scaling granular)
                +
[ Lapisan Infrastruktur / Host ]     -> Instans Mesin Virtual (AWS EC2 / GCP Compute Engine)
                                       (Isolasi tenant keras, batas alokasi resource, kepatuhan keamanan)
```

---

## 7. Analisis FinOps: Efisiensi Biaya dan TCO
Adopsi teknologi kontainer memberikan efisiensi finansial yang signifikan pada struktur TCO perusahaan:
1. **Konsolidasi Perangkat Keras:** Beban kerja yang sebelumnya membutuhkan ~10 server fisik berbasis VM dapat dipadatkan menjadi hanya ~4 server fisik berbasis kontainer (*penghematan CAPEX hardware hingga 60%*).
2. **Penghematan Lisensi:** Menghilangkan keharusan membayar lisensi *Guest OS* dan lisensi hypervisor proprietary berbasis core CPU hingga 80%.
3. **Penurunan Biaya Daya Listrik dan Pendingin (HVAC):** Pengurangan jumlah unit rak server fisik di data center memangkas tagihan listrik dan pendingin operasional (*OPEX hemat hingga 60%*).
4. **Optimasi Densitas:** Memaksimalkan utilisasi rata-rata CPU dan RAM dari yang sebelumnya hanya 15-20% pada server tradisional menjadi 75-80% pada klaster kontainer yang padat.
5. **Presisi Penagihan Pay-per-Use:** Pada public cloud, kontainer memungkinkan penagihan mikro berbasis detik konsumsi komputasi nyata.

---

## 8. Studi Kasus Implementasi Industri
* **E-Commerce Flash Sale:**
  * Tantangan: Lonjakan kunjungan pembeli hingga 10x lipat saat program diskon kilat dimulai.
  * Solusi: Klaster Kubernetes memanfaatkan HPA untuk memicu penskalaan ribuan pod kontainer mikroservis katalog dalam tempo 30 detik tanpa menimbulkan kelambatan pada modul pembayaran transaksi (*checkout gateway*).
* **Sistem Perbankan Digital:**
  * Tantangan: Kebutuhan keamanan regulasi finansial ketat berpadu dengan tuntutan inovasi fitur perbankan yang cepat.
  * Solusi: Menggunakan arsitektur hibrida bertingkat: basis data rekening inti (*core banking*) tetap diisolasi di dalam VM khusus dengan enkripsi keras, sementara aplikasi *mobile banking* dan layanan notifikasi dijalankan di atas kontainer untuk mempercepat siklus rilis fitur baru mingguan.
