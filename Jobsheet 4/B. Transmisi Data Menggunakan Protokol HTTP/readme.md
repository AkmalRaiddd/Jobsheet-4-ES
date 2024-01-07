# B. Transmisi Data Menggunakan Protokol HTTP
   
## 1. Alat dan Bahan
1. Node-RED
2. ESP32
3. XAMPP

## 2. Source Code

1. Code JSON Multi-Protocol IoT Server dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/flow%20program%20Multi-Protocol%20IoT.json">disini</a>
2. Program ESP32 transmisi data dummy menggunakan protokol HTTP metode GET dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/transmisi_data_dummy_keNode-Red_protokol_HTTP_metode_Get/transmisi_data_dummy_keNode-Red_protokol_HTTP_metode_Get.ino">disini</a>
3. Program ESP32 transmisi data dummy menggunakan protokol HTTP metode POST dapat dilihat <a href="https://github.com/AkmalRaiddd/Jobsheet-4-ES/blob/main/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/transmisi_data_dummy_ke_Node-Red_protokol_HTTP_metode_POST/transmisi_data_dummy_ke_Node-Red_protokol_HTTP_metode_POST.ino">disini</a>

## 3. Flow Program

![Flow Program](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/060eca2a-d6ea-4a12-aa60-04f2dc30433f)


## 4. Hasil Percobaan Transmisi Data Dummy Menuju Node-Red Menggunakan Protokol HTTP Metode GET
### Dokumentasi Percobaan

1. Flow chart

   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/18ff4a76-e09f-4237-8bca-3e02503c1998" height=700rem>
   
2. Output serial monitor

   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/133003b2-ea93-42bb-a050-00220ad621c9" width=80% height=80%>
   
4. Debug Node-RED
   
   ![3  Debug Node-RED](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/def8df62-eb6d-4530-aee3-60f087890b69)


5. Dashboard Node-RED

   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/94fdbf38-9e7d-41fb-a5da-84e81c4586fd" width=80% height=80%>
   
7. Tabel database MySQL
   
   ![5  Tabel database MySQL](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/bc8848ea-e7a9-44d7-aece-7bbee2394019)



### Source Code
<img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/97015a8f-597c-450b-95c4-46339ceb4e19" height=1000rem>

### Pembahasan
1. Bagian Awal:
   * Mengimpor pustaka yang dibutuhkan:
     * `WiFi.h` untuk akses fungsi Wi-Fi.
     * `HTTPClient.h` untuk permintaan HTTP.
   * Pendeklarasian variabel:
     * `ssid dan password` untuk menyimpan nama dan kata sandi Wi-Fi.
     * `serverName` untuk menyimpan alamat server yang akan diakses.
     * `lastTime` untuk mencatat waktu terakhir pengiriman data.
     * `timerDelay` untuk mengatur interval pengiriman data (dalam milisekon).
2. Fungsi `setup()`:
   * Inisialisasi Serial Monitor:
     * `Serial.begin(115200)` untuk menampilkan pesan di Serial Monitor.
   * Menghubungkan ke Wi-Fi:
     * `WiFi.begin(ssid, password)` untuk menghubungkan board Arduino ke jaringan Wi-Fi.
   * Menunggu hingga terhubung ke Wi-Fi:
     * Program akan menunggu hingga koneksi Wi-Fi berhasil sebelum melanjutkan.
   * Menampilkan informasi IP Address:
     * Program menampilkan IP Address yang didapatkan oleh board Arduino.
   * Memberi tahu pengaturan timer::
     * Program menampilkan pesan yang menunjukkan interval pengiriman data.
3. Fungsi `loop()`:
   * Mengirim data setiap interval tertentu:
     * Program akan memeriksa apakah waktu yang telah berlalu sejak pengiriman data terakhir melebihi timerDelay. Jika iya, maka akan dilakukan pengiriman data.
   * Memeriksa status koneksi Wi-Fi:
     * Jika board Arduino masih terhubung ke Wi-Fi, maka proses pengiriman data akan dilanjutkan.
   * Membuat client HTTP:
     * `WiFiClient client` membuat objek client untuk komunikasi HTTP.
     * `HTTPClient http` membuat objek untuk melakukan permintaan HTTP.
   * Menentukan server tujuan:
     * `http.begin(client, serverName`) menetapkan server yang akan diakses untuk pengiriman data.
   * Menentukan header Content-Type:
     * `http.addHeader("Content-Type", "application/json")` menetapkan format data yang dikirimkan adalah JSON.
   *Mempersiapkan data yang akan dikirimkan:
     * String `httpRequestData` menyimpan data dalam format JSON yang akan dikirimkan. Dalam kode ini, data yang dikirimkan berupa nilai `dev_id`, `level`, `rainfall`, dan `flow`.
   * Mengirim permintaan HTTP GET:
     * `int httpResponseCode = http.GET()` mengirimkan permintaan GET ke server dengan data yang telah disiapkan.
   * Menampilkan kode respons HTTP:
     * Program menampilkan kode respons yang diterima dari server untuk mengetahui status pengiriman data.
   * Menutup koneksi HTTP:
     * `http.end()` menutup koneksi HTTP.
   * Mencatat waktu pengiriman data terakhir:
     * `lastTime = millis()` menyimpan waktu saat ini sebagai waktu terakhir pengiriman data
       
Catatan:
   * Kode ini menggunakan metode GET.
   * Interval pengiriman data diatur dalam variabel `timerDelay` (5 detik yang digunakan).
   * Data yang dikirimkan dalam format JSON.
   * Server yang dituju adalah `http://192.168.1.7:1880/flood/node1`.

## 5. Hasil Percobaan Transmisi Data Dummy Menuju Node-Red Menggunakan Protokol HTTP Metode POST
### Dokumentasi Percobaan

1. Flow chart 

   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/45a92134-4b8a-4522-837d-8864882a690d" height=700rem>

2. Output serial monitor
 
   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/e7e6774e-e804-483d-9f45-2e42bd6a3831" width=80% height=80%>


3. Debug Node-RED
   
   ![3  Debug Node-RED](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/7a10b336-506f-49d7-9d85-fc4fda49929b)

   
4. Dashboard Node-RED
 
   <img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/addd91a4-7bd8-45f6-a6b8-6c1e9ca4f4db" width=80% height=80%>

### Source Code
<img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/7f590ca2-2693-4bda-8e8a-2af1549a762f" height=1000rem>

### Pembahasan

1. Bagian Awal:
   * Mengimpor pustaka yang dibutuhkan:
     * `WiFi.h` untuk akses fungsi Wi-Fi.
     * `HTTPClient.h` untuk permintaan HTTP.
   * Pendeklarasian variabel:
     * `ssid dan password` untuk menyimpan nama dan kata sandi Wi-Fi.
     * `serverName` untuk menyimpan alamat server yang akan diakses.
     * `lastTime` untuk mencatat waktu terakhir pengiriman data.
     * `timerDelay` untuk mengatur interval pengiriman data (dalam milisekon).
2. Fungsi `setup()`:
   * Inisialisasi Serial Monitor:
     * `Serial.begin(115200)` untuk menampilkan pesan di Serial Monitor.
   * Menghubungkan ke Wi-Fi:
     * `WiFi.begin(ssid, password)` untuk menghubungkan board Arduino ke jaringan Wi-Fi.
   * Menunggu hingga terhubung ke Wi-Fi:
     * Program akan menunggu hingga koneksi Wi-Fi berhasil sebelum melanjutkan.
   * Menampilkan informasi IP Address:
     * Program menampilkan IP Address yang didapatkan oleh board Arduino.
   * Memberi tahu pengaturan timer::
     * Program menampilkan pesan yang menunjukkan interval pengiriman data.
3. Fungsi `loop()`:
   * Mengirim data setiap interval tertentu:
     * Program akan memeriksa apakah waktu yang telah berlalu sejak pengiriman data terakhir melebihi timerDelay. Jika iya, maka akan dilakukan pengiriman data.
   * Memeriksa status koneksi Wi-Fi:
     * Jika board Arduino masih terhubung ke Wi-Fi, maka proses pengiriman data akan dilanjutkan.
   * Membuat client HTTP:
     * `WiFiClient client` membuat objek client untuk komunikasi HTTP.
     * `HTTPClient http` membuat objek untuk melakukan permintaan HTTP.
   * Menentukan server tujuan:
     * `http.begin(client, serverName`) menetapkan server yang akan diakses untuk pengiriman data.
   * Menentukan header Content-Type:
     * `http.addHeader("Content-Type", "application/json")` menetapkan format data yang dikirimkan adalah JSON.
   *Mempersiapkan data yang akan dikirimkan:
     * String `httpRequestData` menyimpan data dalam format JSON yang akan dikirimkan. Dalam kode ini, data yang dikirimkan berupa nilai `dev_id`, `level`, `rainfall`, dan `flow`.
   * Mengirim permintaan HTTP GET:
     * `int httpResponseCode = http.GET()` mengirimkan permintaan GET ke server dengan data yang telah disiapkan.
   * Menampilkan kode respons HTTP:
     * Program menampilkan kode respons yang diterima dari server untuk mengetahui status pengiriman data.
   * Menutup koneksi HTTP:
     * `http.end()` menutup koneksi HTTP.
   * Mencatat waktu pengiriman data terakhir:
     * `lastTime = millis()` menyimpan waktu saat ini sebagai waktu terakhir pengiriman data
       
NB:
   * Kode ini menggunakan metode POST untuk mengirimkan data ke server.
   * Interval pengiriman data diatur dalam variabel `timerDelay` (5 detik yang digunakan).
   * Data yang dikirimkan dalam format JSON.
   * Server yang dituju adalah `http://192.168.1.7:1880/flood/node1`.
   * Kode ini dapat digunakan untuk mengirimkan data sensor atau informasi lain dari board Arduino ke server secara berkala.
