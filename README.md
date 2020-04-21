# **Implementasi Infrastruktur Kafka pada Windows menggunakan Docker-Compose**

## **Beberapa dependency yang dibutuhkan:**

- Docker
- Zookeeper
- Apache Kafka
- Conduktor (Apache Kafka Dekstop Client)

## **Apa itu Apache Kafka?**<br>
![Kafka Infrastructure](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/kafka-connectivity.png)

Apache Kafka merupakan distributed streaming platform yang digunakan untuk mempublikasikan streams of records seperti message queue atau enterprise messaging system, dimana streams of records tersebut disimpan dengan cara yang fault-tolerant.

## **Apa itu Docker?**

Docker merupakan kumpulan platform sebagai produk service yang menggunakan virtualisasi tingkat OS (Operating System) yang memungkinkan eksekusi software dalam packages yang disebut _container_.

## **Implementasi**

### **1) Instalasi Docker**

- Instalasi dapat dilakukan melalui link berikut https://docs.docker.com/docker-for-windows/install/<br>
  ![Docker Webpage](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/instalasi%20docker.jpg)

- Untuk memastikan **Docker** terinstall dengan benar dapat dilakukan check version **Docker** dan **Docker-Compose**
  <br>
  ![Gambar Check Version Docker](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/cek%20versi%20docker.jpg)
  ![gambar check version docker-compose](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/cek%20versi%20docker-compose.jpg)

### **2) Membuat file config (.yml)**

![Gambar file config](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/docker%20config.jpg)

### **3) Menjalankan config**

- Agar dapat menjalankan config untuk membuat zookeeper instance dan kafka instance, gunakan command: <br>
  - `docker-compose -f [nama file config] up`
    untuk menjalankan dalam mode **foreground**<br>
    ![foreground mode](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/foreground%20mode.jpg)
  - `docker-compose -f [nama file config] up -d` untuk menjalankan dalam mode **background** (background process)<br>
    ![background mode](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/background%20mode.jpg)
- Untuk menghentikan eksekusi dari hasil config dapat dilakukan: <br>
  - apabila mode **foreground**, dihentikan dengan menekan CTRL + C (Keyboard Interrupt).<br>
    ![foreground mode stop](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/foreground%20mode%20stop.jpg)
  - apabila mode **background**, dihentikan dengan menjalankan `docker-compose down`.<br>
    ![background mode stop](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/background%20mode%20stop.jpg)
- Selain itu terdapat beberapa command yang dapat dimanfaatkan untuk debugging yaitu:
  - `docker ps` digunakan untuk menampilkan container (proses) yang sedang berjalan.<br>
    ![docker ps](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/docker%20ps.jpg)
  - `docker container ls -a` digunakan untuk menampilkan container yang tersedia (tidak hanya yang sedang berjalan, tetapi state yang lainpun juga).<br>
    ![docker container ls -a](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/docker%20container%20ls%20-a.jpg)
  - `docker container rm [ID Container]` digunakan untuk menghapus container dengan ID tertentu sesuai yang di-input di dalam [ID Container].<br>
    

## **Conduktor sebagai Unit Testing (Apache Kafka Desktop Client)**

- Instalasi Conduktor dapat dilakukan di link berikut https://www.conduktor.io/<br>
  ![Gambar Conduktor](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/instalasi%20conduktor.jpg)
- Apabila instalasi berhasil dan aplikasi terbuka, kita akan diminta untuk login, tampilan yang muncul setelah login berhasil berupa menu utama sebagai berikut<br>
  ![Gambar Menu Utama](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/halaman%20utama.jpg)
- Setelah login berhasil, kita dapat membuat cluster baru, dengan settingan sesuai dengan config (Bootstrap server adalah tempat menginput address Kafka)<br>
  ![Gambar Add Cluster](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/add%20new%20cluster.jpg)
- Apabila input selesai, kita dapat melakukan pengecekan apakah Zookeeper **(Test ZK)** dan Kafka **(Test Kafka Connectivity)** sudah connect, saat berhasil connect akan mendapatkan pop-up seperti berikut<br>
  ![Gambar Popup](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/zookeeper%20connect.jpg)<br>
  ![Gambar Popup](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/kafka%20connect.jpg)
- Setelah itu dilakukan **save** maka akan muncul cluster baru di halaman utama<br>
  ![Gambar cluster baru](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/cluster%20baru.jpg)
- Apabila cluster tersebut dibuka (**click**) dan berhasil melakukan koneksi, maka dashboard akan terbuka dan menampilkan informasi dari cluster tersebut
  ![Cluster dashboard](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/conduktor%20dashboard.jpg)<br>
  ![Cluster broker](https://github.com/DJahvoe/Implementasi-Kafka-dengan-Docker/blob/master/Screenshot/brokers.jpg)
