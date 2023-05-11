# COPY instruction

instruksi yang dapat digunakan untuk menambahkan file dari source ke dalam folder destination di docker image, perbedaan COPY dan ADD adalah jika COPY hanya melakukan copy file saja, sedangkan ADD selain melakukan copy, dia bisa mendownload source dari URL dan juga bisa secara otomatis melakukan extract file kompres

best practinya adalah sebisa mungkin kita menggunakan COPY, jika memang butuh melakukan extract file kompres, gunakan perintah RUN dan jalankan aplikasi untuk extrat file kompres tersebut

## COPY instruction format

```bash
COPY source destination

contoh:
COPY world.txt hello # menambah file world.txt ke folder hello
COPY *.txt hello # menambah semua file .txt ke folder hello
```

## COPY example

Dockerfile

```bash
FROM alpine:latest

RUN mkdir hello
COPY text/*.txt hello

CMD cat "hello/world.txt"
```

![Untitled](COPY%20instruction%200c2c5c7c49614a1abf42c639b5b0c530/Untitled.png)

artinya semua file lokal yang berada di folder text akan di copy ke dalam folder hello di docker image

![Untitled](COPY%20instruction%200c2c5c7c49614a1abf42c639b5b0c530/Untitled%201.png)

build Dockerfile

```bash
docker build -t reiya24/copy 6copy
```

![Untitled](COPY%20instruction%200c2c5c7c49614a1abf42c639b5b0c530/Untitled%202.png)

kita akan menoba membuat container, menjalankannya dan melihat logs dari containernya

```bash
docker container create --name copy reiya24/copy
```

![Untitled](COPY%20instruction%200c2c5c7c49614a1abf42c639b5b0c530/Untitled%203.png)

```bash
docker container start copy
```

![Untitled](COPY%20instruction%200c2c5c7c49614a1abf42c639b5b0c530/Untitled%204.png)

```bash
docker container logs copy
```

![Untitled](COPY%20instruction%200c2c5c7c49614a1abf42c639b5b0c530/Untitled%205.png)