# A. Setting SSID dan Password Wi-Fi ESP32 melalui Web Server

## 1. Alat dan Bahan
1) ESP32
2) Arduino IDE

## 2. Source Code

<img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/36b91886-808b-462e-b6c5-a59c30311128" height=1000rem>


## 3. Flowchart

<img src="https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/4cb2f480-147c-4c94-8ede-4adcbcc3d76b" height=700rem>

## 4. Hasil dan Pembahasan
### Dokumentasi Hasil
1. Tampilan Awal Serial Monitor Sebelum Terhubung

   ![1  Tampilan Awal Serial Monitor Sebelum Dihubungkan](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/bc6ef692-1b0d-4922-9fed-9abb6872d9fe)

2. Tampilan di WiFi dan Web

   ![tampilan wifi](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/2d7b9927-20ba-4cb0-8bfb-b9118376d943
   )
   ![2  tampilan web](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/05f64d50-3906-4004-a62f-f06366779e11)


4. Serial Monitor Setelah Menghubungkan SSID dan PASS

   ![SSID dan Pass](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/f384b73a-0b5b-4bb0-9114-fb380ed652ff)


   ![3  serial monitor setelah menghubungkan ssid dan pass](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/bd20ba64-81be-4f6d-9cb0-f659701ccddc)

   
5. Serial Monitor Sesudah Terhubung

   ![4  Serial Monitor Setelah Berhasil Terhubung](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/bb92a47e-2337-4df6-8dce-d52a649db608)



### Pembahasan
Beberapa kode-kode yang digunakan:
  1. Bagian Awal:
  * Memasukkan pustaka yang diperlukan:
     * 'WiFi.h': Digunakan untuk mengakses fitur Wi-Fi.
     * Membaca kredensial WiFi yang tersimpan di EEPROM.
     * Mencoba menghubungkan ke WiFi menggunakan kredensial tersebut.

  2. Loop Utama:
  * Jika terkoneksi ke WiFi:
    * Menampilkan pesan bahwa telah terkoneksi.
  * Jika tidak terkoneksi ke WiFi:
    * Memeriksa status tombol untuk mengharuskan mode AP (Access Point).
    * Jika tombol tidak ditekan dan koneksi gagal, memulai mode AP dan membuat halaman web untuk konfigurasi WiFi.
    * Menunggu hingga terjadi koneksi ke WiFi.

  3. Fungsi testWifi:
  * Mencoba menghubungkan ke WiFi selama 10 detik.
  * Menjadikan nilai 'true' jika terkoneksi, 'false' jika tidak.

  4. Fungsi launchWeb:
  * Mencetak IP address perangkat terkoneksi .
  * Menjalankan fungsi createWebServer untuk membuat halaman web konfigurasi WiFi.

  5. Fungsi setupAP:
  * Mengatur perangkat sebagai Access Point (AP) dengan nama "MiSREd IoT".
    ![misred](https://github.com/AkmalRaiddd/Jobsheet-4-ES/assets/155884626/4f18667e-b433-4909-829a-9c2139e75d37)

  * Mencari jaringan WiFi di sekitar dan menyimpan daftarnya dalam variabel st.
  * Menjalankan fungsi launchWeb untuk menampilkan halaman konfigurasi WiFi.

  6. Fungsi createWebServer:
  * Menangani permintaan ke halaman web:
    * '/' : Menampilkan halaman utama dengan daftar jaringan WiFi yang ditemukan dan formulir untuk memasukkan kredensial WiFi baru.
    * '/scan' : Memindai ulang jaringan WiFi dan menampilkan hasilnya.
    * '/setting' : Menerima kredensial WiFi baru, menyimpannya ke EEPROM, dan me-restart perangkat.
  
### Kesimpulan:
Kode ini dibuat untuk mempermudah konfigurasi WiFi pada suatu perangkat dengan menyediakan antarmuka web yang dapat diakses dari perangkat lain. Dengan cara ini, pengguna memiliki kemampuan untuk mengubah informasi kredensial WiFi tanpa harus melakukan perubahan langsung pada kode sumber.
