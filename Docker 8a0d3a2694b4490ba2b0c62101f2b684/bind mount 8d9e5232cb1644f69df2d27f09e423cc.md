# bind mount

saat membuat konfigurasi file docker compose, kita bisa tambahkan bind mount menggunakan attribute volume di services, kita juga bisa menambahkan lebih dari satu bind mount

[https://docs.docker.com/compose/compose-file/compose-file-v3/#volumes](https://docs.docker.com/compose/compose-file/compose-file-v3/#volumes)

saat menentukan bind mount, kita bisa menggunakan 2 cara, yaitu short syntax dan long syntax

## short syntax

menggunakan nilai source:target:mode

- source: lokasi di host
- target: lokasi di container
- mode: adalah mode bind mount, ro untuk read only, rw untu read write (default)

source bisa menggunakan relative path dengan diawali .(titik), atau absloute path

contoh volume menggunakan short syntax

## long syntax

kita bisa buat dalam bentuk nested object di volumes dengan attribute:

- type: type mount, volume atau bind
- source: sumber path di host atau nama volume
- target: target path di container
- read_only: flag readolny atau tidak, defaultnya adalah false

contoh bind mount menggunakan short syntax dan long syntax

```bash
version: "3.8"

services:
  mongodb1:
    container_name: mongodb1
    image: mongo:latest
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: reiya
      MONGO_INITDB_ROOT_PASSWORD: reiya
      MONGO_INITDB_ROOT_DATABASE: admin
    volumes:
      - "/home/reiya24/data-mongo:/data/db"
  mongodb2:
      container_name: mongodb2
      image: mongo:latest
      ports:
        - "27018:27017"
      environment:
        MONGO_INITDB_ROOT_USERNAME: reiya
        MONGO_INITDB_ROOT_PASSWORD: reiya
        MONGO_INITDB_ROOT_DATABASE: admin
      volumes:
        - type: bind
          source: "/home/reiya24/data-mongo2"
          target: "/data/db"
          read_only: false
```

![Untitled](bind%20mount%208d9e5232cb1644f69df2d27f09e423cc/Untitled.png)