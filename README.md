# kafka-avro-streaming-processing

Step-step ya sebagai berikut:
1.	Aktifkan zookeeper dan kafka dari confluent docker yang terlah diinstall sebelumnya
 ![image](https://user-images.githubusercontent.com/25885092/227996121-4ac65e70-2f9b-41bb-b733-fdfd01fca608.png)


2.	Pastikan avro sudah terinstall di python env yang digunakan atau istall dengan script berikut:
- pip3 install avro-python3
 ![image](https://user-images.githubusercontent.com/25885092/227996149-a043266b-3f13-4513-8d22-53cc925d27d4.png)


3.	Pastikan source data sudah tersedia di directory yg diinginkan “data/bitcoin_price_Training.csv” didalam directory python file producer yang akan dibuat.
 ![image](https://user-images.githubusercontent.com/25885092/227996287-c1502f94-0cd9-4541-be3c-7413bf6d9c8c.png)


4.	Buat file key schema avro “bitcoin_price_key_train.avsc”:
 ![image](https://user-images.githubusercontent.com/25885092/227996330-c279a4d3-3900-4d2b-b0c7-b70acef233b4.png)

 
5.	Buat juga file value schema avro “bitcoin_price_value_train.avsc”, buat semua kolom menjadi string terlebih dahulu untuk proses bulk insert untuk menghindari conflict tipe data Ketika proses. Data dapat di transform dan di cleansing sesuai kebutuhan setelah data berhasil masuk. Contoh file nya sebagai berikut:
  ![image](https://user-images.githubusercontent.com/25885092/227996377-185dadc8-a605-4136-b48d-8cff50cbab88.png)

 
6.	Buat python producer dengan nama “producer_train.py” (terlampir)
Sesuaikan key_schema dan value_schema yang telah dibuat sebelumnya:
 ![image](https://user-images.githubusercontent.com/25885092/227996425-1802a713-90cf-406d-a8c9-359eb7ae4738.png)

Sesuaikan pula tipe data pada producer:
 ![image](https://user-images.githubusercontent.com/25885092/227996440-60e6ad30-8dde-42bc-badf-24b8666ababb.png)


7.	Buat puthon consumer untuk proses consume data ke big query dengan nama “consumer_train.py” (terlampir), dan sesuaikan path ke google application credential nya:
 ![image](https://user-images.githubusercontent.com/25885092/227996467-950ab845-4f56-4aa6-8151-b0f3e165391b.png)

Setting juga dataset dan design table yang ingin dibuat atau destination dari proses ini:
 ![image](https://user-images.githubusercontent.com/25885092/227996483-7c9c93da-15ce-4f9b-aca9-cb1b2f1587f7.png)

 
8.	Setelah semua persiapan selesai jalankan file python producer dan consumer lewat command prompt atau terminal editor:
 ![image](https://user-images.githubusercontent.com/25885092/227996519-57547ce6-9c9d-4254-a156-92472e0727e6.png)

Setelah producer sukses, jalankan juga file consumer:
 ![image](https://user-images.githubusercontent.com/25885092/227996547-f0061742-eee6-48b7-9237-02eb05658718.png)

 
9.	Setelah kedua proses itu selesai, hasil dapat dilihat pada big query yang menjadi target tadi:
 ![image](https://user-images.githubusercontent.com/25885092/227996573-f841c7e2-3e52-4f5c-89f9-8d921245fe53.png)


#########	Done


