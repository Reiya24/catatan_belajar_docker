# docker network

docker memiliki fitur network yang bisa digunakan untuk membuat jaringan di di dalam docker, sehingga kita bisa mengkoneksikan container dengan container lain dalam satu network yang sama, maka secara otomatis container tersebut bisa saling berkomunikasi

## network driver

saat kita membuat network di docker, kita perlu menentukan driver yang inigin kita gunakan, ada syarat sebuah driver network bisa digunakan:

- bridge : yaitu driver yang digunakan untuk membuat network secara virtual yang memungkinkan container yang terkoneksi di bridge network yang sama saling berkomunikasi
- host : yaitu driver yang digunakan untuk membuat network yang sama dengan sistem host, host hanya jalan di docker linux, tidak bisa digunakan di mac atau windows
- none : yaitu driver untuk membuat network yang tidak bisa berkomunikasi

## melihat network

gunakan perintah:

```bash
docker network ls
```

## membuat network

gunakan perintah:

```bash
docker netowork create --driver nama_driver nama_network
```

![Untitled](docker%20network%201b5f41bc734c4d6292c555339f723fca/Untitled.png)

bila kita tidak mendefinisikan nama bridge secara default akan menggunakan network bridge

## menghapus network

sebelum menghapus network, kita harus menghapus containernya terlebih dahulu dari network, bila sudah, gunakan perintah

```bash
docker network rm nama_network
```

![Untitled](docker%20network%201b5f41bc734c4d6292c555339f723fca/Untitled%201.png)