# HEALTHCHECK instruction

adalah instruksi untuk mengecek apakah container masih berjalan dengan baik atau tidak.

jika terdapat HEALTHCHECK, secara otomatis container akan memiliki status health, yang bernilai starting, healty, dan unhealty

## HEALTHCHECK instruction

```bash
HEALTHCHECK NONE #tidak ada pengecekan healthcheck
HEALTHCHECK [OPTIONS] CMD command
options:
--interval=DURATION (default:30s) # seberapa sering command healthcheck dieksekusi
--timeout=DURATION (default:30s) # jika 30 detik tidak ada respon, maka dianggap timeout
--start-period=DURATION (default: 0s) #jeda pertama kali pengecekan ketika container baru dijalankan
--retries=N (default: 3) # sebarapa banyak percobaan bila terjadi gagal
```

## HEALTHCHECK instruction

Dockerfile:

```bash
FROM golang:1.18-alpine

RUN apk --no-cache add curl
RUN mkdir app

COPY main.go app

EXPOSE 8080

HEALTHCHECK --interval=5s --start-period=5s CMD curl -f http://localhost:8080/health

CMD go run app/main.go
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled.png)

file main.go

```bash
package main

import (
	"fmt"
	"net/http"
)

var counter = 0

func main() {
	http.HandleFunc("/", HelloServer)
	http.HandleFunc("/health", HealthCheck)

	http.ListenAndServe(":8080", nil)
}

func HealthCheck(w http.ResponseWriter, r *http.Request) {
	counter = counter + 1
	if counter > 5 {
		w.WriteHeader(500)
		fmt.Fprintf(w, "KO")
	} else {
		fmt.Fprintf(w, "OK")
	}
}

func HelloServer(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hello, World!")
}
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled%201.png)

*logic aplikasinya adalah aplikasi memiliki url /health yang digunakan untuk healthcheck. bila variable counter lebih dari 5, maka status http menjadi 500

build dockerfile:

```bash
docker build -t reiya24/health 14health
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled%202.png)

buat docker container

```bash
docker container create --name health -p 8080:8080 reiya24/health
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled%203.png)

jalankan docker container

```bash
docker container start health
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled%204.png)

jalankan docker container

```bash
docker container ls
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled%205.png)

kita bisa melihat detail dari healthcheck menggunakan container inspect

```bash
docker container inspect health
```

![Untitled](HEALTHCHECK%20instruction%2048e9d9fe717844e6abdb9bd34261a789/Untitled%206.png)