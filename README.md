# 🌐 Sistem Monitoring Ruangan Real-time (IoT)

Proyek ini adalah sistem monitoring kualitas udara dan cuaca ruangan secara real-time menggunakan mikrokontroler **ESP8266**, sensor **DHT11**, dan **MQ135** yang terintegrasi penuh ke web server berbasis **CodeIgniter 4** menggunakan visualisasi grafik interaktif **Chart.js**.

---
## 🚀 Panduan Instalasi Proyek

Ikuti langkah-langkah di bawah ini untuk melakukan instalasi dan konfigurasi proyek pada perangkat keras (Hardware/IoT) dan server lokal (Web) Anda.

## 🛠️ Langkah-Langkah Instalasi & Konfigurasi Sistem

Ikuti panduan berikut secara berurutan untuk menjalankan proyek dari sisi hardware hingga website:

### 1. 📥 Clone Repository dan Pindahkan ke Folder Web Server

* Clone repository proyek:

    ```bash
    git clone https://github.com/busyrajalal/monitoring-ruang.git
    ```

* Pindahkan folder hasil clone ke direktori web server.

    **XAMPP:**
    
        ```text
        C:\xampp\htdocs\
        ```
    
    Sehingga struktur folder menjadi:
    
        ```text
        htdocs/
        └── monitoring-ruang/
        ```

### 2.🔌 Konfigurasi Hardware (ESP8266 / Arduino IDE)
Sebelum mengunggah kode program ke NodeMCU ESP8266, buka file program di folder `monitoring-ruangan\file database dan ino\monitoring-ruang` menggunakan aplikasi Arduino IDE, lalu sesuaikan konfigurasi jaringan dan server berikut:

*   **Koneksi Wi-Fi:** Cari baris kode berikut dan sesuaikan dengan SSID serta password Wi-Fi di lokasi Anda agar alat bisa terhubung ke internet:
    ```cpp
    const char* ssid     = "Nama WiFi";
    const char* password = "Password";
    const char* host     = "IP Kalian";
    ```
*   **Target Pengiriman URL API:** Cari fungsi pengiriman data HTTP Request (`HTTPClient`) dan sesuaikan alamat IP Laptop/Server lokal Anda yang menjalankan CodeIgniter 4:
    ```cpp
      String Link = "http://" + String(host) + "/monitoring-ruangan/terima-data/" 
                  + String(suhu, 1) + "/" 
                  + String(hum, 0) + "/" 
                  + String(gas) + "/" 
                  + String(ppm_co2, 1) + "/" 
                  + String(ppm_amonia, 1) + "/" 
                  + String(ppm_benzena, 1) + "/" 
                  + String(ppm_alkohol, 1) + "/" 
                  + String(ppm_asap, 1);
    ```

### 3. 🗄️ Import Database MySQL
*   Buka browser Anda dan akses kontrol panel database lokal di alamat: `http://192.168.x.x/phpmyadmin/`.
*   Buat database baru dengan nama bebas (contoh: `dhtmq`).
*   Masuk ke database baru tersebut, pilih menu **Import** di bagian atas.
*   Klik *Choose File* dan pilih file database **`dhtmq.sql`** yang ada di folder `monitoring-ruangan\file database dan ino` proyek ini.
*   Gulir ke bawah dan klik tombol **Import / Go**. Pastikan semua tabel (`sensor`) berhasil terbuat.

### 4. 🌐 Konfigurasi Website CodeIgniter 4 (`.env`)
Buka folder source code website `monitoring-ruangan/` menggunakan text editor (VS Code / Notepad++), lalu lakukan konfigurasi berkas lingkungan:

*   Jika berkas masih bernama `env`, ubah namanya terlebih dahulu menjadi **`.env`** (tambahkan tanda titik di depannya).
*   Buka file `.env` tersebut, cari bagian konfigurasi **App URL** dan sesuaikan dengan alamat IP lokal komputer Anda saat ini:
    ```env
    //Contoh IP :
    app.baseURL = 'http://192.168.1.229/monitoring-ruangan/'
    ```
*   Gulir ke bawah ke bagian **Database**, lalu sesuaikan nama database, username, serta password MySQL Anda:
    ```env
    database.default.hostname = 'localhost'
    database.default.database = 'dhtmq'  # Sesuaikan dengan nama DB yang di-import tadi
    database.default.username = 'root'
    database.default.password = ''     
    database.default.DBDriver = 'MySQLi'
    ```

---

