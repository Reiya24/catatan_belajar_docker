# Tentang Docker Compose

adalah tool hyang digunakan untuk menjalankan docker container secara sekaligus menggunakan file YAML untuk melakukan konfigurasi Docker Containernya.

## fitur Docker compose

memiliki multiple isolated environment dalam satu docker host/server, sehingga memungkinkan kita untuk bisa membuat banyak sekali jenis environment untuk Docker Compose.

Docker compose bisa mendeteksi container mana yang harus dibuat & tidak perlu dibuat ulang dari perubahan file konfigurasi

## kapan menggunakan docker compose

- Membuat development environment. ketika sedang mendevelop aplikasi, kita butuh tool-tool berbeda untuk setiap project, kita bisa gunakan docker compose untuk melakukan setup nya
- Automated Testing, kadang ketika kita membuat automation testing, banyak sekali hal yang harus kita jalankan secara manual, Docker compose bisa membantu kita untuk otomatisasi proses setupnya
- Deployment, Docker compose juga bisa digunakan untuk deployment aplikasi, jadi ktia tidak perlu lakukan start manual aplikasi ktia di server, cukup jalankna menggunakan docker compose