# monitor docker event

untuk  melihat kejadian apa saja yang terjadi di docker secara realtime, kita bisa menggunakan perintah

```bash
docker events
```

contohnya kita bisa memonitor kejadian yang terjadi pada sebuah container dengan perintah:

```bash
docker events --filter 'container=nama_container'
```

![Untitled](monitor%20docker%20event%206298dc9ff4d74f3f91cf3225ba5259de/Untitled.png)

tidak ada output yang keluar sampai kita melakukan sesuatu pada container tersebut, contohnya saat kita membuat sebuah container tersebut, maka akan muncul lognya

![Untitled](monitor%20docker%20event%206298dc9ff4d74f3f91cf3225ba5259de/Untitled%201.png)