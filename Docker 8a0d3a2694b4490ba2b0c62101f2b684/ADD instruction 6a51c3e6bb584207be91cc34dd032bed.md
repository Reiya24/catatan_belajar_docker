# ADD instruction

instruction ini digunakan untuk menambahkan file dari source ke dalam folder destination di Docker Image

perintah ADD bisa mendeteksi file source,  yaitu file kompres seperti tar.gz, gzip, dll. jika terdeteksi file source merupakan file kompres, maka secara otomatis file tersebut akan di extract ke dalam folder destination

perintah ADD juga bisa mendukung banyak penambahan file sekaligus

penambahan banyak file sekaligus di instruksi ADD menggunakan pattern di golang [https://pkg.go.dev/path/filepath#Match](https://pkg.go.dev/path/filepath#Match)

## ADD instruction format

```bash
ADD source destination

contoh:
ADD world.txt hello # menambahkan file world.txt ke folder hello
ADD *.txt hello # menambahkan semua file yang berekstensi .txt ke folder hello
```

## example ADD

Dockerfile

```bash
FROM alpine:latest

RUN mkdir hello
ADD text/*.txt hello

CMD cat "hello/world.txt"
```

![Untitled](ADD%20instruction%206a51c3e6bb584207be91cc34dd032bed/Untitled.png)

artinya semua file lokal yang berada di folder text akan di copy ke dalam folder hello di docker image

![Untitled](ADD%20instruction%206a51c3e6bb584207be91cc34dd032bed/Untitled%201.png)

Build Dockerfile:

```bash
docker build -t reiya24/add 5add
```

![Untitled](ADD%20instruction%206a51c3e6bb584207be91cc34dd032bed/Untitled%202.png)

kita akan menoba membuat container, menjalankannya dan melihat logs dari containernya

```bash
docker container create --name add reiya24/add
```

![Untitled](ADD%20instruction%206a51c3e6bb584207be91cc34dd032bed/Untitled%203.png)

```bash
docker container start add
```

![Untitled](ADD%20instruction%206a51c3e6bb584207be91cc34dd032bed/Untitled%204.png)

```bash
docker container logs add
```

![Untitled](ADD%20instruction%206a51c3e6bb584207be91cc34dd032bed/Untitled%205.png)