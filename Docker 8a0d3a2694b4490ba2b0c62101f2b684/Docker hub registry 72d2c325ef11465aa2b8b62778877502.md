# Docker hub registry

adalah salah satu layanan docker registry yang berfungsi untuk menyimpan image yang sudah kita buat.

untuk mengupload docker image kita ke dockerhub registry, pastikan sudah mempunyai akun terlebih dahulu

## Contoh proses upload docker image ke Dockerhub registry

### menggunakan password

lakukan proses login pada terminal, lalu masukan password

```bash
docker login -u username_dockerhub
```

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled.png)

### menggunakan access token

masuk ke [pengaturan dockerhub](https://hub.docker.com/settings/security), pilih new access token

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled%201.png)

masukan deskripsi access token, sesuaikan perizinan, lalu klik generate

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled%202.png)

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled%203.png)

*jangan lupa simpan akses token di tempat yang aman, karena akses token hanya dapat dilihat sekali

lakukan proses login pada terminal, lalu masukan access token yang ada di dockerhub

```bash
docker login -u username_dockerhub
```

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled%204.png)

## mengupload image ke dockerhub / push docker image

gunakan perintah

```bash
docker push username_dockerhub/nama_image:tag
```

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled%205.png)

docker image berhasil di push ke dockerhub

![Untitled](Docker%20hub%20registry%2072d2c325ef11465aa2b8b62778877502/Untitled%206.png)