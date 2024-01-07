# C. Transmisi Data Menggunakan Protokol MQTT

## 1. Alat dan Bahan
1. Node-RED
2. ESP32
3. XAMPP

## 2. Source Code

1. Code JSON Multi-Protocol IoT Server dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/flow%20program%20Multi-Protocol%20IoT.json">disini</a>
2. Program ESP32 dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/C.%20Transmisi%20Data%20Menggunakan%20Protokol%20MQTT/program%20transmisi%20mqtt/program%20transmisi%20mqtt.ino">disini</a>


## 3. Flow Program
![Flow Program](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/48fd9699-126d-4f10-8ff8-f851184f8d8b)


## 4. Hasil & Pembahasan
### Dokumentasi Hasil

1. Flow chart 

   ![Flow Chart](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/1f28c26d-f7bc-437e-b970-2665d0f702a3)

   
2. Output serial monitor
   
   ![2  Output serial monitor](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/cb50579e-53a7-4bab-aa1c-4c85c871e77d)


3. Debug Node-RED
   
   ![3  Debug Node-RED](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/7d82911d-691a-43db-ac5e-d6440862c7a6)

   
4. Dashboard Node-RED

   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/1159a8d6-f7d5-41f4-a91b-c67be28b918c" width=80% height=80%>
   
5. Tabel database MySQL
   
   ![image](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/b9dd7061-ad8c-4d36-80bf-26274ccae6eb)



### Source Code
![Penjelasan Kode](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/2dc0c044-953a-4a2d-a392-83c2bd99c4ec)


### Pembahasan
1. Bagian Awal:
   * Memasukkan library yang diperlukan:
     * `WiFi.h` untuk mengakses fungsi Wi-Fi.
     * `PubSubClient.h` untuk komunikasi MQTT.
     * `ArduinoJson.h` untuk menangani format JSON.
   * Deklarasi variabel:
     * `ssid` dan `password` untuk menyimpan nama dan password Wi-Fi.
     * `mqtt_server` untuk menyimpan alamat server MQTT.
     * `espClient` untuk membuat koneksi TCP/IP ke server MQTT.
     * `client` untuk komunikasi MQTT.

2. Fungsi `setup_wifi()`:
   * Menghubungkan board Arduino ke jaringan Wi-Fi dengan nama dan password yang telah ditentukan.
   * Menampilkan informasi IP Address yang didapatkan oleh board Arduino.
     
3. Fungsi `reconnect()`:
   * Mencoba menghubungkan board Arduino ke server MQTT.
   * Jika gagal, mencoba kembali setiap 5 detik.

4. Fungsi `setup()`:
   * Menginisialisasi Serial Monitor untuk menampilkan pesan.
   * Menghubungkan board Arduino ke Wi-Fi.
   * Mengatur server MQTT yang akan dituju

5. Fungsi loop():
   * Memeriksa apakah koneksi MQTT masih tersambung.
   * Jika terputus, memanggil fungsi `reconnect()` untuk menyambung kembali.
   * Menangani proses MQTT secara berkala.
   * Mempersiapkan data yang akan dikirimkan dalam format JSON.
   * Menerbitkan data ke topic "flood/node1" pada server MQTT.
   * Menunggu 10 detik sebelum mengirimkan data berikutnya.

Catatan:
   * Kode ini menggunakan protokol MQTT untuk mengirimkan data sensor atau informasi lain dari board Arduino ke server secara berkala.
   * Interval pengiriman data diatur dalam fungsi `loop()` (10 detik yang digunakan).
   * Data yang dikirimkan dalam format JSON.
   * Server MQTT yang digunakan adalah `broker.hivemq.com`.
   * Kode ini dapat digunakan untuk aplikasi IoT yang membutuhkan komunikasi dua arah yang ringan dan efisien.
