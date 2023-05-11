# environment variable

saat membuat konfigurasi file docker compose, kita bisa tambahkan environment variable dengan menggunakan attribute environment

contoh environment variable untuk image mongodb

```bash
version: "3.8"

services:
  mongodb-example:
    image: mongo:latest
    container_name: mongodb-example
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: reiya
      MONGO_INITDB_ROOT_PASSWORD: reiya
      MONGO_INITDB_DATABASE: admin
```

![Untitled](environment%20variable%2000161722da2e49e0a64ae59554bbda5a/Untitled.png)