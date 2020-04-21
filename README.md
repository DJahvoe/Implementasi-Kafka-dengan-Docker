# **Implementasi Infrastruktur Kafka pada Windows menggunakan Docker-Compose**

## **Beberapa dependency yang dibutuhkan:**

- Docker
- Zookeeper
- Apache Kafka
- Conduktor (Apache Kafka Dekstop Client)

## **Apa itu Apache Kafka?**

Apache Kafka merupakan distributed streaming platform yang digunakan untuk mempublikasikan streams of records seperti message queue atau enterprise messaging system, dimana streams of records tersebut disimpan dengan cara yang fault-tolerant.

## **Apa itu Docker?**

Docker merupakan kumpulan platform sebagai produk service yang menggunakan virtualisasi tingkat OS (Operating System) yang memungkinkan eksekusi software dalam packages yang disebut _container_.

## **Implementasi**

### **1) Instalasi Docker**

- Instalasi dapat dilakukan melalui link berikut https://docs.docker.com/docker-for-windows/install/<br>
  [Gambar Web Docker]

- Untuk memastikan **Docker** terinstall dengan benar dapat dilakukan check version **Docker** dan **Docker-Compose**
  <br>
  [Gambar Check Version Docker][gambar check version docker-compose]

### **2) Membuat file config (.yml)**

[Gambar file config]

### **3) Menjalankan config**

- Agar dapat menjalankan config untuk membuat zookeeper instance dan kafka instance, gunakan command: <br>
  - `docker-compose -f [nama file config] up`
    untuk menjalankan dalam mode **foreground**
  - `docker-compose -f [nama file config] up -d` untuk menjalankan dalam mode **background** (background process)
- Untuk menghentikan eksekusi dari hasil config dapat dilakukan: <br>
  - apabila mode **foreground**, dihentikan dengan menekan CTRL + C (Keyboard Interrupt).
  - apabila mode **background**, dihentikan dengan menjalankan `docker-compose down`.
- Selain itu terdapat beberapa command yang dapat dimanfaatkan untuk debugging yaitu:
  - `docker ps` digunakan untuk menampilkan container (proses) yang sedang berjalan.
  - `docker container ls -a` digunakan untuk menampilkan container yang tersedia (tidak hanya yang sedang berjalan, tetapi state yang lainpun juga).
  - `docker container rm [ID Container]` digunakan untuk menghapus container dengan ID tertentu sesuai yang di-input di dalam [ID Container].

### **4) Conduktor sebagai Unit Testing (Apache Kafka Desktop Client)**

- Instalasi Conduktor dapat dilakukan di link berikut https://www.conduktor.io/<br>
  [Gambar Conduktor]
- Apabila instalasi berhasil dan aplikasi terbuka, kita akan diminta untuk login, tampilan yang muncul setelah login berhasil berupa menu utama sebagai berikut<br>
  [Gambar Menu Utama]
- Setelah login berhasil, kita dapat membuat cluster baru, dengan settingan sesuai dengan config (Bootstrap server adalah tempat menginput address Kafka)<br>
  [Gambar Add Cluster]
- Apabila input selesai, kita dapat melakukan pengecekan apakah Zookeeper **(Test ZK)** dan Kafka **(Test Kafka Connectivity)** sudah connect, saat berhasil connect akan mendapatkan pop-up seperti berikut<br>
  [Gambar Popup]
- Setelah itu dilakukan **save** maka akan muncul cluster baru di halaman utama<br>
  [Gambar cluster baru]
- Apabila cluster tersebut dibuka (**click**) dan berhasil melakukan koneksi, maka dashboard akan terbuka dan menampilkan informasi dari cluster tersebut
