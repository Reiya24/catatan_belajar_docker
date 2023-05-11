# container network

setelah kita membuat network, kita bisa menambahkan container ke network

contianer yang terdapat di dalam network yang sama bisa saling berkomunikasi (tergantung jenis driver networknya)

container bisa mangakses container lain dengan menyebutkan hostname dari containernya, yaitu nama containernya

## membuat container dengan network

untuk menambahkan container ke network, kita bisa menambahkan perintah —network ketika membuat container

```bash
docker container create --name nama_container --network nama_network image:tag
```

![Untitled](container%20network%20bf7c8870323d48ffac99de8d526a54e9/Untitled.png)

## menghapus container dari network

```bash
	docker network disconnect nama_network nama_container
```

![Untitled](container%20network%20bf7c8870323d48ffac99de8d526a54e9/Untitled%201.png)

## menambahkan container ke network

```bash
docker network connect nama_network nama_container
```

![Untitled](container%20network%20bf7c8870323d48ffac99de8d526a54e9/Untitled%202.png)