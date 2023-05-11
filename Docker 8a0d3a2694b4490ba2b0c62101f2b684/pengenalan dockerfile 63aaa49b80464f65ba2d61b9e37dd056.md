# pengenalan dockerfile

dockerfile berfungsi untuk membuat docker image kita sendiri, pembuatan docker image bisa dilakukan dengan menggunakan instruksi yang kita simpan di dalam file yang diberinama Dockerfile.

jadi Dockerfile adalah file text yang berisi semua perintah yang bisa kita gunakan untuk membuat docker image

## docker build

untuk membuat docker image dari dockerfile, kita bisa menggunakan perintah “docker build”.

saat membuat docker image dengan docker build, nama image secara otomatis akan dibuat random 

namun biasanya kita ingin menambahkan nama atau tag pada imagenya, kita bisa mengubahnya dengan menambahkan perintah -t

contoh cara menggunakan docker build:

```bash
	docker build -t username_dockerhub/nama_image:tag folder_dockerfile
```

![Untitled](pengenalan%20dockerfile%2063aaa49b80464f65ba2d61b9e37dd056/Untitled.png)

untuk membuat image lebih dari satu file, kita bisa build menggunakan contoh berikut:

```bash
docker build -t username_dockerhub/nama_image:tag -t username_dockerhub/nama_image:tag folder_dockerfile
```

![Untitled](pengenalan%20dockerfile%2063aaa49b80464f65ba2d61b9e37dd056/Untitled%201.png)