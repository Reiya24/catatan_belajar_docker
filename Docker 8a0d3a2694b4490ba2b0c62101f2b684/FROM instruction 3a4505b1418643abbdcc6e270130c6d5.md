# FROM instruction

saat kita membuat docker image, biasanya perintah pertama adalah melakukan build stage dengan instruksi FROM

FROM digunakan untuk membuat build stage dari image yang kita tentukan, karena biasanya jarang sekali kita membuat Docker image dari scrath (kosongan), biasanya kita membuat dari docker image lain yang sudah ada.

untuk menggunakan FROM, kita bisa gunakan perintah:

```bash
FROM image:version
```

![Untitled](FROM%20instruction%203a4505b1418643abbdcc6e270130c6d5/Untitled.png)

## build Dockerfile

```bash
docker build -t username_dockerhub/nama_image:tag lokasi_dockerfile
```

![Untitled](FROM%20instruction%203a4505b1418643abbdcc6e270130c6d5/Untitled%201.png)