# 🚀 Panduan Instalasi Proyek

Ikuti langkah-langkah di bawah ini untuk melakukan instalasi dan konfigurasi proyek pada perangkat keras (Hardware/IoT) dan server lokal (Web) Anda.

## 🛠️ Langkah-Langkah Instalasi

### 1. Konfigurasi Perangkat (Hardware / Arduino)
* Buka file dengan ekstensi `.ino` menggunakan **Arduino IDE**.
* Cari bagian konfigurasi jaringan di dalam kode.
* Ubah data berikut sesuai dengan jaringan Anda:
  * **SSID** (Nama WiFi)
  * **Password WiFi**
  * **IP Address** (Sesuaikan dengan IP server lokal Anda)
* Lakukan *compile* dan *upload* kode ke mikrokontroler Anda.

### 2. Konfigurasi Server Lokal (Web)
* Pindahkan seluruh folder proyek ini ke dalam direktori server lokal Anda (misal: `C:/xampp/htdocs/`).
* Cari file bernama `env` di dalam folder tersebut.
* Ubah nama file `env` menjadi `.env` (perhatikan tanda titik di awal).
* Buka file `.env` tersebut menggunakan teks editor.
* Cari baris konfigurasi IP, lalu **ganti IP Address** tersebut agar sesuai dengan IP komputer/server yang Anda gunakan.

---
💡 **Catatan:** Pastikan perangkat IoT dan komputer server Anda terhubung ke dalam jaringan WiFi yang sama agar dapat saling berkomunikasi.
