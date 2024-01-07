# D. Akuisi Data dan Kendali Perangkat IoT Menggunakan Protokol MQTT
   
## 1. Alat dan Bahan
1. Node-RED
2. ESP32
3. Kabel jumper
4. LED
5. XAMPP

## 2. Source Code

1. Code JSON Multi-Protocol IoT Server dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/flow%20program%20Multi-Protocol%20IoT.json">disini</a>
2. Program ESP32 kontrol nyala LED melalui dashboard Node-RED dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/D.%20Akuisi%20Data%20dan%20Kendali%20Perangkat%20IoT%20Menggunakan%20Protokol%20MQTT/akuisisi/akuisisi.ino">disini</a>

## 3. Flow Program

![Flow Program](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/f36724a3-a0c8-44e6-9b8e-14a1d1084072)


## 4. Hasil & Penjelasan Percobaan Kontrol Nyala LED Melalui Dashboard Node-RED
### Dokumentasi Percobaan

1. Flow Program 
   
  ![Flow Program](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/a1296840-be4d-40da-a0ab-9a8f1b2baa33)


2. Dokumentasi
   
   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/1ed693d4-113b-4bf8-bdc8-3454632a3a71" width=40% height=40%>   
     
   ![2  Dokumentasi](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/ae302f4f-c2db-4602-893a-f99cc044e8be)


3. Debug Node-RED
   
   ![3  Debug Node-RED](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/a8390e35-86a0-4c79-9b81-327ba892090f)


   
4. Dashboard Node-RED

   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/9833ab0b-298f-4493-81c5-696a7ed47887" width=40% height=40%>
   
### Kode
<img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/43420306-1c61-46a9-9f75-e86d02de1ea8" height=1000rem>

### Pembahasan
1. Bagian Awal:
   * Memasukkan library yang diperlukan:
     * `WiFi.h` untuk mengakses fungsi Wi-Fi.
     * `Adafruit_MQTT.h` dan `Adafruit_MQTT_Client.h` untuk komunikasi MQTT dengan server Adafruit IO.
   * Deklarasi variabel:
     *`WLAN_SSID`, `WLAN_PASS`, `AIO_SERVER`, `AIO_SERVERPORT`, `AIO_USERNAME`, dan `AIO_KEY` untuk konfigurasi koneksi Wi-Fi dan MQTT.
     * `output` untuk menyimpan pin output yang akan dikendalikan.
     * `client` untuk membuat koneksi TCP/IP ke server MQTT.
     * `mqtt` untuk komunikasi MQTT.
     * `led` untuk berlangganan topic "led" pada server MQTT.

2. Fungsi `setup()`:
   * Menginisialisasi Serial Monitor untuk menampilkan pesan.
   * Mengatur pin 2 sebagai output.
   * Menghubungkan board Arduino ke jaringan Wi-Fi.
   * Menampilkan informasi IP Address yang didapatkan oleh board Arduino.
   * Berlangganan topic "led" pada server MQTT.
     
3. Fungsi `loop()`:
   * Mencoba menghubungkan board Arduino ke server MQTT jika belum terhubung.
   * Membaca pesan yang diterima dari topic yang dilanggan setiap 5 detik.
   * Jika pesan diterima dari topic "led":
     * Menampilkan nilai pesan yang diterima.
     * Jika nilai pesan adalah "1", menyalakan LED pada pin 2.
     * Jika nilai pesan bukan "1", mematikan LED pada pin 2.

4. Fungsi `MQTT_connect()`:
   * Mencoba menghubungkan board Arduino ke server MQTT.
   * Jika gagal, mencoba kembali hingga maksimal 3 kali dengan jeda 5 detik.
   * Jika gagal terhubung setelah 3 kali, menghentikan program.
     
NB:
   * Kode ini menggunakan protokol MQTT untuk mengendalikan perangkat IoT (dalam hal ini, menyalakan dan mematikan LED) dari jarak jauh melalui server Adafruit IO.
   * Server MQTT yang digunakan adalah `io.adafruit.com`.
   * Kode ini dapat dimodifikasi untuk mengendalikan berbagai macam perangkat IoT lainnya.
