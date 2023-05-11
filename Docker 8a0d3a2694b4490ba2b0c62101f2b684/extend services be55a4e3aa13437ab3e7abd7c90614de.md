# extend services

yaitu fitur dimana kita bisa melakukan merge beberapa file konfigurasi sekaligus.

saat menjalankan docker compose, kita bisa gunakan perintah -f nama_file.yaml jika ingin menggunakan nama file yang bukan docker-compose.yaml

contoh:

file docker compose.yaml

```bash
version: "3.8"

services:
  app:
    container_name: app
    build:
      context: "./app"
      dockerfile: Dockerfile
    image: "app-golang:1.0.0"
    environment:
      - "APP_PORT=8080"
    ports:
      - "8080:8080"
```

file production.yaml

```bash
version: "3.8"

services:
  app:
    environment:
      - "MODE=local"
```

![Untitled](extend%20services%20be55a4e3aa13437ab3e7abd7c90614de/Untitled.png)

untuk melakukan build menggunakan 2 file docker compose, kita bisa gunakan perintah

```bash
docker compose -f docker-compose.yaml -f production.yaml create &&
docker compose -f docker-compose.yaml -f production.yaml start
```

![Untitled](extend%20services%20be55a4e3aa13437ab3e7abd7c90614de/Untitled%201.png)