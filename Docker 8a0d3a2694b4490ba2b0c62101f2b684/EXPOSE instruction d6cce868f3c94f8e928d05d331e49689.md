# EXPOSE instruction

EXPOSE adalah instruksi untuk memberitahu bahwa container akan listen port pada nomor dan protocol tertentu

instruksi EXPOSE tidak akan mempublish port apapun, ia hanya digunakan sebagai dokumentasi untuk memberitahu yang membuat docker container, bahwa docker image ini akan menggunakan port tertentu ketika dijalankan Docker Container

## EXPOSE instruction format

```bash
EXPOSE port #defaultnya menggunakan TCP
EXPOSE port/tcp
EXPOSE PORT/udp
```

## EXPOSE example

Dockerfile

```bash
FROM golang:1.18-alpine

RUN mkdir app
COPY main.go app

EXPOSE 8080

CMD go run app/main.go
```

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled.png)

file main.go yang dimana program tersebut berjalan di port 8080

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

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%201.png)

build Dockerfile

```bash
docker build -t reiya24/expose 8expose
```

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%202.png)

inspect docker image yang sudah di build

```bash
docker image inspect reiya24/expose
```

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%203.png)

bila kita scroll kebawah maka akan terlihat metadata yang bernama “ExposedPorts” bernilai 8080/tcp

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%204.png)

buat docker container menggunakan image yang sudah di build

```bash
docker container create --name expose --publish 8080:8080 reiya24/expose
```

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%205.png)

jalankan docker container

```bash
docker container start expose
```

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%206.png)

aplikasi go sudah berjalan

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%207.png)

![Untitled](EXPOSE%20instruction%20d6cce868f3c94f8e928d05d331e49689/Untitled%208.png)