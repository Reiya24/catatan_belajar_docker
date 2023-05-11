# LABEL instruction

instruksi LABEL merupakan isntruksi yang digunakan untuk menambahkan metada ke dalam docker image yang kita buat, metadata hanya berguna sebagai informasi saja, seperti nama aplikasi, pembuat, website, lisensi dan lain lain, tidak akan digunakan ketika kita menjalankan docker container

## LABEL instruction format

```bash
LABEL key=value key2=value2
```

## example LABEL

Dockerfile:

```bash
FROM alpine:latest

LABEL author="reiya tenggara" company="dumbways" website="reiya24.com"

RUN mkdir hello
RUN echo "hello world" > "hello/world.txt"
CMD cat "hello/world.txt"
```

![Untitled](LABEL%20instruction%20db9b24e4817e4199826b1c2bc97ef7f2/Untitled.png)

build Dockerfile:

```bash
docker build -t reiya24/label 4label
```

![Untitled](LABEL%20instruction%20db9b24e4817e4199826b1c2bc97ef7f2/Untitled%201.png)

inspect docker image yang sudah di build:

```bash
docker image inspect reiya24/label
```

![Untitled](LABEL%20instruction%20db9b24e4817e4199826b1c2bc97ef7f2/Untitled%202.png)

scroll kebawah, maka kita akan menemukan metadata yang sebelumnya sudah kita definisikan

![Untitled](LABEL%20instruction%20db9b24e4817e4199826b1c2bc97ef7f2/Untitled%203.png)