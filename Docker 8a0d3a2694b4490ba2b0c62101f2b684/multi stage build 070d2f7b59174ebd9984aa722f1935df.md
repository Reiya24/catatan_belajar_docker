# multi stage build

## masalah dengan image size

saat kita membuat dockerfile dari base image yang besar, secara otomatis ukuran Image nya pun akan menjadi besar juga, oleh karena itu, usahakan selalu gunakan base image yang memang kita butuhkan saja, jangan terlalu banyak menginstall fitur di image yang tidak digunakan

![Untitled](multi%20stage%20build%20070d2f7b59174ebd9984aa722f1935df/Untitled.png)

*base image golang memiliki ukuran yang besar

## Contoh solusi dengan image size besar pada program go lang

Go-lang memiliki fitur untuk melakukan kompilasi kode program menjadi binary file, sehingga tidak membutuhkan image go-lang lagi.

## Multi Stage build

Docker memiliki fitur Multi Stage build, dimana dalam Dockerfile, kita bisa membuat beberapa build stage/tahapan build.

di dalam Dockerfile, kita bisa menggunakan beberapa instruksi FROM, setiap instruksi FROM, artinya itu adalah build stage.

buid stage di awal biasanya digunakan untuk melakukan persiapan seperti melakukan proses kompilasi,  buid stage terakhir biasanya digunakan untuk membuat doker image seperti menjalankan aplikasi yang sudah di kompilasi

## Multi Stage build example

Dockerfile

```bash
FROM golang:1.18-alpine as builder
WORKDIR /app/
COPY main.go /app/
RUN go build -o /app/main /app/main.go

FROM alpine:3
WORKDIR /app/
COPY --from=builder /app/main /app/
CMD /app/main
```

![Untitled](multi%20stage%20build%20070d2f7b59174ebd9984aa722f1935df/Untitled%201.png)

*as builder adalah nama alias untuk build stage pertama
pada baris ke delapan, build stage kedua akan menggambil file yang berada di /app/main yang ada di build stage pertama, dan disalin ke folder /app yang kedua

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

![Untitled](multi%20stage%20build%20070d2f7b59174ebd9984aa722f1935df/Untitled%202.png)

build dockerfile

```bash
docker build -t reiya24/multi 16multi
```

![Untitled](multi%20stage%20build%20070d2f7b59174ebd9984aa722f1935df/Untitled%203.png)

hasil docker image akan lebih kecil

```bash
docker image ls | grep "multi"
```

![Untitled](multi%20stage%20build%20070d2f7b59174ebd9984aa722f1935df/Untitled%204.png)