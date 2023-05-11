# container exec

saat kita membuat container, aplikasi yang terdapat di dalam container hanya bisa diakses dari dalam container, oleh karena itu, kita perlu masuk ke dalam containernya itu sendiri, kita dapat menggunakan fitur container exec, dimana ia digunakan untuk mengeksekusi kode program yang terdapat di dalam container

## masuk ke container

untuk masuk ke dalam container, ktia bisa mencoba mengeksekusi program bash script yang terdapat di dalam container dengan bantuan container exec

```bash
docker container exec -i -t nama_container /bin/bash
```

![Untitled](container%20exec%2028631c59350a4f5b9b4c256b0bf45f9b/Untitled.png)

-i adalah argument interaktif, menjaga input tetap aktif

-t adalah argument untuk alokasi pseudo-TTY (terminal akses)

/bin/bash contoh kode program yang terdapat di dalam container