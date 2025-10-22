# TeknologiIoTSemesterGanjil2025
Tugas mata kuliah Teknologi IoT Semester 5 2025 oleh Muhammad Bagaskara(2042231017) dan Galuh Pandu Satrio(2042231019)

# Implementasi Sensor DS18B20 untuk Monitoring Temperatur Air pada Budidaya Hidroponik Berbasis ESP32-S3 dan OTA-Updates

## Deskripsi Proyek

Proyek ini mengimplementasikan sensor DS18B20 untuk monitoring temperatur air pada sistem budidaya hidroponik. Mikrokontroler yang digunakan adalah ESP32-S3 dengan bahasa pemrograman Rust. Data suhu dikirimkan ke platform ThingsBoard menggunakan protokol MQTT dan divisualisasikan secara real-time. Selain itu, sistem dilengkapi dengan fitur pembaruan firmware melalui OTA (Over-The-Air) untuk mempermudah pemeliharaan perangkat.

## Fitur

* Monitoring suhu air secara real-time
* Visualisasi data telemetry melalui dashboard ThingsBoard
* Komunikasi data menggunakan protokol MQTT
* Mekanisme OTA Updates untuk pembaruan firmware jarak jauh
* Integrasi sensor DS18B20 dengan ESP32-S3
* Implementasi dalam bahasa pemrograman Rust

## Komponen Perangkat Keras

* ESP32-S3
* Sensor DS18B20 (probe waterproof)
* Resistor pull-up 4.7 kΩ
* Adaptor 5V

## Perangkat Lunak

* Rust Programming Language
* Cargo
* Crate ds18b20 dan onewire
* ThingsBoard Cloud
* GNUplot (untuk analisis latensi)

## Instalasi dan Setup

1. Instal Rust melalui terminal:

   ```
   curl https://sh.rustup.rs -sSf | sh
   rustc --version
   ```
2. Instal dependensi ESP32-S3 untuk Rust:

   ```
   cargo install espup espflash
   rustup target add xtensa-esp32s3-none-elf
   ```
3. Tambahkan crate sensor DS18B20 pada Cargo.toml:

   ```
   ds18b20 = "0.7"
   onewire = "0.4"
   ```
4. Sesuaikan kode `main.rs` dengan SSID Wi-Fi, password, dan token ThingsBoard.
5. Kompilasi proyek:

   ```
   cargo build --release
   ```
6. Flash firmware ke ESP32-S3 menggunakan espflash.
7. Buat akun di ThingsBoard dan daftarkan perangkat.
8. Buat dashboard dan tambahkan widget grafik real-time untuk memvisualisasikan suhu.

## OTA Update

1. Upload file firmware hasil kompilasi ke GitHub.
2. Tambahkan widget push button di ThingsBoard.
3. Atur payload JSON:

   ```
   {"fw_url":"https://github.com/username/repo/releases/download/v1.0.0/firmware.bin"}
   ```
4. Tekan tombol OTA untuk memperbarui firmware perangkat.
5. Status update dapat dilihat melalui shared attributes di ThingsBoard.

## Struktur Direktori

```
.
├── src/
│   └── main.rs
├── Cargo.toml
├── README.md
└── firmware/
    └── firmware.bin
```

## Pengujian

* Pengiriman data diuji dengan ThingsBoard telemetry
* Latensi dihitung menggunakan perbandingan RTC dan cloud timestamp
* OTA update diuji melalui dashboard ThingsBoard
* GNUplot digunakan untuk menganalisis data historis

## Lisensi

Proyek ini dibuat untuk keperluan akademik dan dapat dikembangkan lebih lanjut untuk implementasi komersial dalam sistem pertanian hidroponik berbasis IoT.

---

Apakah kamu ingin saya tambahkan contoh **perintah flashing ESP32-S3** dan **setup MQTT di ThingsBoard** juga pada README ini? (supaya lebih lengkap untuk publik GitHub)
