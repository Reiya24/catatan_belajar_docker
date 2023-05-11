# pengenalan Docker dan Container

Docker adalah salah satu layanan container manager. Container berfungsi untuk membundling dan mengisolasi semua aplikasi dan depedensi yang diperlukan. Berbeda dengan virtual machine, Container dapat melakukan itu semua tanpa harus menginstall ulang sistem operasi. Karena container tersebut dijalankan menggunakan sistem operasi dimana Container manager itu berjalan.
berikut adalah Perbandinan perbedaan virtual machine dan container

Virtual machine : 

![Untitled](pengenalan%20Docker%20dan%20Container%20ad40f7337f9b48a4b04fc6c3d238b81f/Untitled.png)

Container :

![Untitled](pengenalan%20Docker%20dan%20Container%20ad40f7337f9b48a4b04fc6c3d238b81f/Untitled%201.png)

## permasalahan menggunakan virtual machine

masalah ketika kita menggunakan VM adalah prosesnya yang lambat, mulai dari pembuatan VM, proses waktu booting / me-restart VM. Serta VM memerlukan resource yang lebih besar besar

## Container

berbeda dengan VM, container berfokus pada sisi aplikasi, Container sebenarnya berjalan diatas aplikasi container manager yang berjalan di sistem operasi, pada kasus kita kali ini container manager tersebut adalah docker. dan Container akan menggunakan sistem operasi host dimana container manaegrnya berjalan, oleh karena itu, container lebih hemat resource dan lebih cepat saat proses menjalankannya