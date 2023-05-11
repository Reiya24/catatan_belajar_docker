# container volume

volume yang sudah kita buat, bisa kita gunakan di container.

keuntungan menggunaakan volume adalah, jika container kita hapus, data akan tetap aman di volume

cara menggunakan volume di container sama dengan menggunakan bind mount, ktia bisa menggunakan parameter —mount, namun dengan menggunakan type volume dan source nama volume

## membuat container volume

```bash
docker container create --name test_mysql --mount \
"type=volume,source=mysql_volume,destination=/var/lib/mysql" \
--env MYSQL_ROOT_PASSWORD='reiya' \
--env MYSQL_USER='reiya' \
--env MYSQL_PASSWORD='reiya' \
--publish 3306:3306 \
mysql:latest
```

![Untitled](container%20volume%20f7053203293b42a6b50abb705a25a45d/Untitled.png)