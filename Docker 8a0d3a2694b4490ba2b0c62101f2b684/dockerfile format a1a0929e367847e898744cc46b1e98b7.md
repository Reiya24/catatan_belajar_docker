# dockerfile format

Dockerfile biasanya dibuat dalam sebuah file dengan nama “Dockerfile”, walaupun sebenarnya bisa saja kita membuat dengan nama lain, namun tetap direkomendasikan menggunakan nama “Dockerfile”

## instruction format

secara sederhana berikut adalah format untuk file Dockerfile:

```bash
#komentar
INSTRUCTION arguments
```

- “#” digunakan untuk menambah komentar, kode dalam baris tersebut tidak akan dieksekusi
- “INSTRUCTION” adalah perintah yang digunakan di Dockerfile, ada banyak perintah yang tersedia, dan penulisan perintahnya tidak case sensitive, sehingga bebas mau gunakan huruf besar/kecil. namun rekomendasinya adalah menggunakan UPPERCASE
- “arguments” adalah data argument untuk INSTRUCTION, yang menyesuaikan dengan jenis INSTRUCTION yang digunakan