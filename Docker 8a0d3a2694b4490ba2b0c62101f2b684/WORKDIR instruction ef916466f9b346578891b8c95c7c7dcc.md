# WORKDIR instruction

adalah instruksi untuk menentukan direktori / folder untuk menjalankan instruksi RUN, CMD, ENTRYPOINT, COPY dan ADD, lokasi direktori akan otomatis dibuat bila sebelumnya tidak ada

setelah menentukan lokasi WORKDIR, direktori tersebut akan dijadikan tempat menjalankan instruksi selanjutnya

jika lokasi WORKDIR adalah relative path, maka secara otomatis dia akan masuk ke direktori dari WORKDIR sebelumnya

WORKDIR juga bisa digunakan sebagai path untuk lokasi pertama kali ketika kita masuk ke dalam Docker Container

 

## WORKDIR instruction format

```bash
WORDKIR /app #wordkirnya adalah /app
WORDIR docker #sekarang workdirnya adalah /app/docker
WORKDIR /home/app #sekarang workdirnya adalah /home/app
```

## WORKDIR example

Dockerfile

```bash
FROM golang:1.18-alpine

WORKDIR /app
COPY main.go /app

EXPOSE 8080
CMD go run main.go
```

![Untitled](WORKDIR%20instruction%20ef916466f9b346578891b8c95c7c7dcc/Untitled.png)

file main.go

```bash
package main

import (
	"fmt"
	"net/http"
)

func main() {
	http.HandleFunc("/", HelloServer)
	http.ListenAndServe(":8080", nil)
}

func HelloServer(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hello, World!")
}
```

![Untitled](WORKDIR%20instruction%20ef916466f9b346578891b8c95c7c7dcc/Untitled%201.png)

build Dockerfile

```bash
docker build -t reiya24/workdir 11workdir
```

![Untitled](WORKDIR%20instruction%20ef916466f9b346578891b8c95c7c7dcc/Untitled%202.png)

buat container dari image yang sudah di build

```bash
docker container create --name workdir -p 8080:8080 reiya24/workdir
```

![Untitled](WORKDIR%20instruction%20ef916466f9b346578891b8c95c7c7dcc/Untitled%203.png)

jalankan docker container

```bash
docker container start workdir
```

![Untitled](WORKDIR%20instruction%20ef916466f9b346578891b8c95c7c7dcc/Untitled%204.png)

masuk ke dalam container

```bash
docker container exec -i -t workdir /bin/sh
```

![Untitled](WORKDIR%20instruction%20ef916466f9b346578891b8c95c7c7dcc/Untitled%205.png)