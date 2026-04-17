# 🕌 Imsakiyah WhatsApp Bot (High-Performance Edition)

<p align="center">
  <img src="assets/logo.png" alt="Imsakiyah Bot Logo" width="150"/>
</p>

Imsakiyah Bot adalah solusi WhatsApp berbasis *serverless* yang memberikan jadwal salat presisi dan pencarian masjid terdekat secara real-time. Versi ini telah dioptimalkan untuk skalabilitas tinggi dengan sistem caching dan perlindungan API.

## 🚀 Fitur Unggulan Terbaru

* **Smart Caching System:** Mengurangi latensi dan penggunaan kuota API hingga 90% menggunakan `CacheService`. Data jadwal salat disimpan selama 6 jam berdasarkan koordinat wilayah (grid 1.1km).
* **Graceful Rate Limit Handling:** Dilengkapi pendeteksi *Error 429 (Too Many Requests)*. Jika API eksternal sibuk, bot akan memberikan respon edukatif kepada user, bukan sekadar diam atau error.
* **Enterprise Geocoding:** Menggunakan Google Native Maps Engine yang lebih stabil dan cepat dibandingkan provider open-source lainnya.
* **Multi-Language Engine (i18n):** Mendukung 9 bahasa secara otomatis berdasarkan kode negara nomor WhatsApp atau pilihan manual melalui command `/lang`.
* **Zero-Trust Security:** Webhook dilindungi oleh *secret query parameter* dan seluruh kredensial disimpan dalam `PropertiesService` (Environment Variables), bukan dalam kode mentah.


## 🛠️ Arsitektur Sistem
1.  **VS Code:** Lingkungan pengembangan utama.
2.  **Clasp:** Menjembatani kode lokal dengan Google Cloud Environment.
3.  **Google Apps Script:** Engine serverless yang memproses logika bisnis.
4.  **Google Sheets:** Database ringan untuk menyimpan preferensi bahasa dan log transaksi.
5.  **Meta WhatsApp Cloud API:** Gateway komunikasi utama ke pengguna.

## 📦 Cara Instalasi & Update

### Prasyarat
- Node.js & NPM
- Google `clasp` terinstal secara global (`npm install -g @google/clasp`)

### Langkah Setup
1. Clone repositori ini.
2. Hubungkan dengan project Apps Script Anda:
   ```bash
   clasp clone "YOUR_SCRIPT_ID"

3. Konfigurasi kredensial melalui fungsi setupSecurity() di Code.js, lalu jalankan sekali di editor browser.
4. Deploy aplikasi
   ```bash
   clasp push
   clasp deploy -i "YOUR_DEPLOYMENT_ID"

🔒 Keamanan Webhook
Pastikan URL Webhook yang didaftarkan di Meta Developer Portal menyertakan kunci rahasia Anda:
https://script.google.com/.../exec?secret=PASSWORD_RAHASIA_ANDA

📄 Lisensi
Distribusi bebas untuk tujuan edukasi dan komunitas.
