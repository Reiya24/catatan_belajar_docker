# health check

secara default container yang dibuat, baik itu secara manual ataupun docker compose, pasti akan selalu menggunakan healt check yang dibuat di Dockerfile.

namun kita bisa mengubah Health Check di file konfigurasi docker compose pada attribute healthcheck di services

health heck memiliki banyak attribute :

- test: berisikan cara melakukan test health check
- interval: interval melakukan health check
- timout: timout melakukan health check
- retries: total retry ketika gagal
- start_period: waktu mulai menggunakan health check

contoh penggunaan health check:

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
    healthcheck:
      test: [ "CMD", "curl", "-f", "http://localhost:8080/health" ]
      interval: 5s
      timeout: 5s
      retries: 3
      start_period: 5s
```

![Untitled](health%20check%20e5f37dac569647be8d7fb3a1916f19a2/Untitled.png)