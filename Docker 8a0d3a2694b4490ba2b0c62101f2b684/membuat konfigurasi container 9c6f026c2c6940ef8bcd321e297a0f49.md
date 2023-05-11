# membuat konfigurasi container

kita bisa membuat container menggunakan configuration file di docker compose menggunakan file yaml,

kita bisa tambahkan bagian services untuk menentukan container name dan image untuk docker container yang akan kita buat

```bash
version: "3.8"

services:
  nginx-container:
    container_name: nginx-container
    image: nginx:latest
  redis-container:
    container_name: redis-container
    image: redis:latest
```

![Untitled](membuat%20konfigurasi%20container%209c6f026c2c6940ef8bcd321e297a0f49/Untitled.png)

setelah membuat konfigurasi file, kita buat containernya menggunakan docker compose, yaitu dengan perintah

```bash
docker compose create
```

![Untitled](membuat%20konfigurasi%20container%209c6f026c2c6940ef8bcd321e297a0f49/Untitled%201.png)

container berhasil dibuat

![Untitled](membuat%20konfigurasi%20container%209c6f026c2c6940ef8bcd321e297a0f49/Untitled%202.png)

*jika kita menjalankan docker compose create namun container sudah ada, maka docker tidak akan membuat ulang container tersebut