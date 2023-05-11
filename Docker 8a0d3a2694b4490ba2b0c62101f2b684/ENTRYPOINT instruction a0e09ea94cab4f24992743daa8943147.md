# ENTRYPOINT instruction

adalah instruksi untuk menentukan executable file yang akan di jalankan oleh container.

saat kita membuat instruksi CMD tanpa executable file, secara otomatis CMD akan menggunakan ENTRYPOINT

## ENTRYPOINT instruction format

```bash
ENTRYPOINT ["executable", "param1", "param2"]
ENTRYPOINT executable param1 param2
saat menggunakan CMD ["param1", "param2"], maka pram tersebut akan dikirim ke ENTRYPOINT
```

## ENTRYPOINT example

Dockerfile

```bash
FROM golang:1.18-alpine

RUN mkdir /app/
COPY main.go /app/

EXPOSE 8080

ENTRYPOINT ["go", "run"]

CMD ["/app/main.go"]
```

![Untitled](ENTRYPOINT%20instruction%20a0e09ea94cab4f24992743daa8943147/Untitled.png)

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

![Untitled](ENTRYPOINT%20instruction%20a0e09ea94cab4f24992743daa8943147/Untitled%201.png)

build Dockerfile

```bash
docker build -t reiya24/entrypoint 15entrypoint
```

![Untitled](ENTRYPOINT%20instruction%20a0e09ea94cab4f24992743daa8943147/Untitled%202.png)

inspect docker image

```bash
docker image inspect reiya24/entrypoint
```

![Untitled](ENTRYPOINT%20instruction%20a0e09ea94cab4f24992743daa8943147/Untitled%203.png)

scroll kebawah, maka kita akan melihat entrypoint berisi perintah executable

![Untitled](ENTRYPOINT%20instruction%20a0e09ea94cab4f24992743daa8943147/Untitled%204.png)