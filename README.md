# Jarkom-Modul-1-D10-2022

## Anggota Kelompok:
|Nama     |NRP    |
|----------|-------|
|Hasna Lathifah Purbaningdyah|5025201108|
|Anggito Anju Hartawan Manalu|5025201216|
|Hidayatullah|5025201031|

## 1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 
Jawaban : Web server yang digunakan adalah `nginx/1.10.3`. Kami menggunakan display filter `http` dan melihat salah satu paket respons yang diberikan dimana dalam headernya terdapat informasi tentang web server yang digunakan.

<img width="800" alt="Server: nginx/1.10.3" src="https://user-images.githubusercontent.com/80145586/192101387-d35b84dc-3624-4aaa-8a47-491f5aec2f35.png">

## 2. Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?
Jawaban: **Evaluasi unjuk kerja User Space Filesystem (FUSE)**

Langkah:
Memfilter packet request berisi “detail” dengan display filter `http.request.uri contains "detail"`

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192101850-dfc6e073-24f2-4f55-978e-9aa42766abc8.png">

Dari packet tersebut didapatkan link detail topik beserta no topiknya (194)

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192101879-4433f359-41b9-40e0-8239-089fe03bf5d1.png">

`Follow > HTTP` dan mencari kemana link tersebut merujuk dalam file html websitenya.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192101907-f967b4e8-4284-4020-a50b-81974cfdcd11.png">

Didapatkan Judul Topiknya 

### Alternatif:
`File > Export Objects > HTTP...` lalu cari sesuai no topik yg didapatkan (194). 

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102030-2862d9aa-8147-4f6c-b7a0-6e184cc47546.png">

Save dan tambahkan extensi `.html` pada filenya. Lalu dibuka

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102064-b494b748-6b36-4f00-9e13-af95a01c28ac.png">


## 3. Filter sehingga wireshark hanya menampilkan paket yang menuju port 80
Jawaban: Display filter: `tcp.dstport == 80`

Menggunakan `dstport` karena mencari paket yang menuju ke suatu port.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102217-9020b62f-08f7-4914-9095-d1906327a9c3.png">

## 4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21
Jawaban: Capture filter: `src port 21`
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102474-a941e7f6-b459-403e-a93c-975898c1577a.png">

Display filter: `tcp.srcport == 21 || udp.srcport == 21`

Menggunakan `srcport` karena mencari paket yang berasal dari suatu port.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102486-cc20d91a-a96f-4c83-aec3-1831ac154412.png">

## 4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21
Jawaban: Capture filter: `src port 443`
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102570-8c7f7185-3b7a-47ea-949f-845b41bd3678.png">

Display filter: `tcp.srcport == 443 || udp.srcport == 443`

Menggunakan `srcport` karena mencari paket yang berasal dari suatu port.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102580-3ab3cd1c-6655-4b5d-9b81-a6be3c68d2dd.png">



## 6. Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id !
Jawaban : Memperoleh ip address dari `lipi.go.id` menggunakan `ping lipi.go.id` dalam cmd.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102635-575a5c3f-e428-4020-9713-7cf5d98763e9.png">

Display filter : ip.dst == 203.160.128.158
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102668-7b4b5fa4-67fe-4254-8054-6dc22373dbc7.png">

## 7. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian
Jawaban: Dapatkan Ip terlebih dahulu, salah satu caranya dengan menggunakan command ping ke suatu ip yang dipilih melalui cmd. Disini menggunakan `Ping 1.1.1.1`
<img width="400" alt="image" src="https://user-images.githubusercontent.com/80145586/192102823-e1b597e7-60a2-4268-b6c9-4616a8be722f.png">

Mendapatkan ip asal dari paket yang menuju 1.1.1.1 dengan command `ip.dst == 1.1.1.1`.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102874-0df143e0-c8f1-4ca0-a9db-209f0d0468c1.png">

Lalu mengcapture dengan capture filter `src host [ip kalian]`
(disini dengan ip 192.168.216.23)
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192102922-f3143d01-dba5-4e33-8e84-fb5de0ba57a1.png">

## 8. Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.
Jawaban : 
- Melihat paket tcp dan sort dari lengthnya
- Dapat diobservasi bahwa semua paket tcp dengan length yang panjang berasal dari ip 127.0.0.1 dan 127.0.1.1
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103048-9399a444-66e2-4ca1-b2b7-181c3ee59daf.png">

- Memfilter menggunakan `ip.addr == 127.0.0.1 && ip.addr == 127.0.1.1`
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103066-0453f14b-f275-4d4e-b7f8-96f6ebbd2306.png">

- Dapat ditemukan 5 tcp stream, Follow tcp stream untuk melihat isinya. 2 diantara memiliki info yang relevan.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103083-073ece08-263b-48f0-a046-bc056ccddeb1.png">
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103088-d3ffd273-c326-45e8-9e3d-a429d0d4e103.png">

- Dari percakapan tersebut ditemukan beberapa clue:
  - File salt akan dikirim melalui port 9002
  - Password ada hubungannya dengan kesamaan dari nama kelima karakter dari suatu anime tentang kembar lima. Dari sini dapat ditebak password merupakan nama belakang kelima karakter yaitu `nakano` dan password berupa lowercase.
  - File salt akan di-*decrypt* menggunakan openssl dengan metode des3

## 9. Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.
Jawaban:
- Dari clue yang didapat, file salt dapat dicari dengan command `tcp.port == 9002 && frame matches "salt"`. `matches` digunakan karena ia *case-insensitive*. 
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103557-5a280323-307e-47d0-9f1c-2a9710d1afd3.png">

- `Follow > TCP Stream` dan ubah dalam bentuk RAW.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103665-ac5fad19-a570-4b55-a04f-79ce6ffb8611.png">

-  Kemudian kita dapat melakukan Save Data tersebut dengan nama file [nama_kelompok].des3. Pada hal ini file akan dinamakan D10.des3.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103676-ab19ed98-aed8-4b8d-b98b-8a056ad577fd.png">

- Kemudian kita akan melakukan decrypt dari file `D10.des3` dengan menggunakan openssl dengan metode decrypt des3 dengan key nakano. Di dalam wsl command line kita dapat menuliskan command: `openssl des3 -d -salt -in D10.des3 -k nakano -out flag.txt`. Hal ini bertujuan untuk menyimpan output dari hasil decrypt pada file `flag.txt` seperti gambar di bawah.
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103716-9cc4aa35-db50-428c-b0b8-98df820f13d5.png">

## 10. Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!
Jawaban: JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80145586/192103780-9ee14ced-3258-48e7-97ac-0da520730074.png">
