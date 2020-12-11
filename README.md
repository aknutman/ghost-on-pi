# ghost-on-pi

Dear Pembaca Setia,
Kali ini Penulis hendak berbagi pengalaman terkait instalasi [Ghost Blog](https://ghost.org/) di Raspberry Pi. Penulis menggunakan Raspberry Pi 4b saat instalasi, namun Raspberry Pi 3b seharusnya sudah cukup.

Tutorial kali ini menggunakan [Docker](https://www.docker.com/) untuk instalasi Ghost, karena sangat memudahkan dalam migrasi maupun instalasi kembali di tempat baru. Bagi yang belum mengetahui tentang Docker, dapat mengikuti link [berikut](https://www.docker.com/). Pada dasarnya Docker adalah Environment yang terisolasi, sehingga memberikan jaminan Environment yang sama untuk implementasi aplikasi ke PC / Server, di berbagai OS (Mac / Unix / PC).

**Disclaimer**
```
Tutorial kali ini adalah instalasi untuk di *Local Environment*, yang hanya bisa diakses di jaringan lokal, misal di rumah yang ada WiFi nya.
```

----
# Environment Preparation
Sebelum mulai untuk Instalasi, kita pastikan dulu package yang ada di RPi terupdate, dengan menjalankan perintah berikut di Terminal:
> `sudo apt-get update && sudo apt-get upgrade`

Kemudian lakukan instalasi Docker, dengan menjalankan perintah
> `curl -sSL https://get.docker.com | sh`

Kemudian jadikan user Pi sebagai member dari group Docker
> `sudo usermod -aG docker pi`

Dan lakukan instalasi Python3 Pip untuk penggunaan Docker Compose
> `sudo apt-get -y install python3-pip`

Baru kita dapat menginstal Docker Compose
> `sudo pip3 install docker-compose`

----
# Instalation Preparation
Berikutnya kita akan memerlukan folder untuk menyimpan konfigurasi untuk instal Ghost, yaitu konfigurasi berbentuk file `*.yaml` yang dapat didownload di [github ini](https://github.com/aknutman/ghost-on-pi/blob/master/docker-compose.yaml).

Pastikan untuk mengubah `url: http://ext.local` menjadi `url: http://IP_LOCAL_SENDIRI`, atau konfigurasi dns di router (lain kesempatan akan penulis sampaikan) sehingga menjadi mirip sebuah domain seperti punya penulis.

Berikutnya, di Terminal masuk ke folder yang ada file `docker-compose.yaml` tadi, dan jalankan
> `docker-compose up -d`

Dan, semua selesai... 

Bila nanti ada kelanjutan cerita terkait backup, ataupun di-publish ke internet, akan penulis sampaikan di lain kesempatan.

Salam blogging...
