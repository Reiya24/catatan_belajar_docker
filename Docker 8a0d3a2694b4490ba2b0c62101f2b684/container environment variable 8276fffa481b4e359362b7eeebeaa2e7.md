# container environment variable

Dengan environment variable, kita bisa mengubah-ubah konfigurasi aplikasi, tanpa harus mengubah kode aplikasinya lagi.
Docker container memiliki parameter yang bisa kita gunakan untuk mengirim environment variable ke aplikasi yang terdapat di dalam docker container

## menambahkan environment variable

untuk menambah envonment variable, kita bisa menggunakan perintah —env atau -e, misal:

```bash
docker container create --name nama_container --env key=value --env key2=value image:tag
```

### contoh kasus

saya akan membuat docker container yang berisikan image mysql, image mysql memiliki beberapa environment variable, saya akan memasukan environment variable untuk root password, user, dan user password

```bash
docker container create --name test_mysql \
--env MYSQL_ROOT_PASSWORD='reiya' \
--env MYSQL_USER='reiya' \
--env MYSQL_PASSWORD='reiya' \
mysql:latest
```