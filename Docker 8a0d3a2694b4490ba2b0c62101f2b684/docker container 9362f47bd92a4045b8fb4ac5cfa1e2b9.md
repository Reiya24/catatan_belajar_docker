# docker container

Jika docker image seperti installer aplikasi, maka docker ocntainer mirip seperti aplikasi hasil installernya

Satu docker image bisa digunakan untuk membuat beberapa docker container, asalkan nama docker containernya berbeda

jika kita sudah membuat docker container, ,maka docker image yang digunakan tidak bisa dihapus,, hal ini dikarenakan sebenarnya docker container tidak meng-copy isi docker image, tapi hanya menggunakan isinya saja

## membuat container

untuk membuat container, cukup gunakan perintah:

```bash
docker container create --name nama_contianer nama_image:tag
```

![Untitled](docker%20container%209362f47bd92a4045b8fb4ac5cfa1e2b9/Untitled.png)

## menjalankan container

gunakan perintah

```bash
docker container start nama_container
```

![Untitled](docker%20container%209362f47bd92a4045b8fb4ac5cfa1e2b9/Untitled%201.png)

selain menggunakan nama container, kita juga bisa menjalankan container dengan menggunakan container id

## melihat container

untuk melihat container yang sedang berjalan, gunakan perintah:

```bash
docker container ls
```

![Untitled](docker%20container%209362f47bd92a4045b8fb4ac5cfa1e2b9/Untitled%202.png)

untuk melihat semua contianer baik yang sedang berjalan atau tidak, gunakan perintah:

```bash
docker container ls -a
```

![Untitled](docker%20container%209362f47bd92a4045b8fb4ac5cfa1e2b9/Untitled%203.png)

## menghentikan container

gunakan perintah:

```bash
docker container stop nama_container
```

![Untitled](docker%20container%209362f47bd92a4045b8fb4ac5cfa1e2b9/Untitled%204.png)

## menghapus container

sebelum menghapus container, kita harus menghentikan containernya terlebih dahulu, bila sudah, gunakan perintah

```bash
docker container rm nama_container
```

![Untitled](docker%20container%209362f47bd92a4045b8fb4ac5cfa1e2b9/Untitled%205.png)