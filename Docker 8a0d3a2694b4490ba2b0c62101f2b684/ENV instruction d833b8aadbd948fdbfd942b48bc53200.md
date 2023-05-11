# ENV instruction

Environment variable (ENV) adalah instruksi yang digunakan untuk mengubah environment variable, baik itu ketika tahapan build atau ketika jalan dalam Docker Container

ENV yang sudah di definisikan di dalam Dockerfile bisa digunakan kembali dengan menggunakan syntaks ${NAMA_ENV}

environment variable yang dibuat menggunakan instruksi ENV disimpan di dalam docker image dan bisa dilihat menggunakan perintah docker image inspect

selain itu, environment variable juga bisa diganti nilainya ketika pembuatan docker container dengan perintah

```bash
docker container create --env key=value
```

## ENV instruction format

```bash
ENV key=value
ENV key1=value1 key2=value2
```

## ENV example

Dockerfile, terdapat default value APP_PORT berinlai 8080, namun bisa kita definisikan saat sedang menbuat container

```bash
FROM golang:1.18-alpine

ENV APP_PORT=8080

RUN mkdir app
COPY main.go app

EXPOSE ${APP_PORT}

CMD go run app/main.go
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled.png)

file main.go, terdapat variable port yang berfungsi untuk menyimpan port yang akan kita definisikan 

```bash
package main

import (
	"fmt"
	"net/http"
	"os"
)

func main() {
	port := os.Getenv("APP_PORT")
	fmt.Println("Run app in port : " + port)
	http.HandleFunc("/", HelloServer)
	http.ListenAndServe(":"+port, nil)
}

func HelloServer(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hello, World!")
}
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%201.png)

build Dockerfile

```bash
docker build -t reiya24/env 9env
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%202.png)

inspect docker image

```bash
docker image inspect reiya24/env
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%203.png)

bila kita scroll kebawah, maka ada informasi mengenai Environment dari docker image

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%204.png)

buat container dengan environment variable APP_PORT bernilai 9090

```bash
docker container create --name env --env APP_PORT=9090 -p 9090:9090 reiya24/env
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%205.png)

jalankan docker container

```bash
docker container start env
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%206.png)

lihat log dari container

```bash
docker container logs env
```

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%207.png)

![Untitled](ENV%20instruction%20d833b8aadbd948fdbfd942b48bc53200/Untitled%208.png)