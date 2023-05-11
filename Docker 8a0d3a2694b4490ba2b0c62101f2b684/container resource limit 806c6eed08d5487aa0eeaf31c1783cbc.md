# container resource limit

saat membuat container, secara default dia akan menggunakan semua resource yang diberikan ke docker, namun kita bisa memberikan resource limit container tersebut

## memory

untuk menentukan jumlah memory pada container yang akan dibuat, gunakan perintah —memory diikuti dengan angka memory yang diperbolehkan untuk digunakan

kita bisa menambahkan ukuran dalam bentuk:

- b (bytes)
- k (kilo bytes)
- m (mega bytes)
- g (giga bytes)

misal : 100m artinya 100 mega bytes

## CPU

untuk menentukan berapa jumlah CPU pada container yang akan dibuat, gunakan perintah —cpus diikuti dengan jumlah core

misalkan jika kita set dengan nilai 1.5, maka container bisa menggunakan satu setengah CPU core

## contoh kasus

membuat sebuah docker image dengan limit memory 100 megabytes dan cpu setengah core

```bash
docker container create --name small_nginx --publish 8321:80 --memory 100m --cpus 0.5 \
nginx:latest
```

![Untitled](container%20resource%20limit%20806c6eed08d5487aa0eeaf31c1783cbc/Untitled.png)