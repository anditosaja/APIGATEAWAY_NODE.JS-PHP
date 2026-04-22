# APIGATEAWAY_NODE.JS-PHP
Sistem API Gateway berbasis Node.js (Express) yang menghubungkan dua layanan berbeda:

1. Service 1 (Node.js) = Layanan Manajemen Mahasiswa
2. Service 2 (PHP) = Layanan Manajemen Produk

Semua request dari client hanya melalui API Gateway (port 3000).

## Arsitektur Sistem

Client tidak langsung mengakses service, melainkan melalui gateway seperti berikut:

Client → API Gateway (3000) → Service 1 (3001) / Service 2 (3002)

## Teknologi yang Digunakan

Pastikan sudah terinstall:

1. Node.js
2. Express.js
3. http-proxy-middleware
4. PHP (Native / Built-in Server)

## Instalasi

Masuk ke folder project, lalu install dependency:

npm install express http-proxy-middleware

## Struktur Folder
api-gateway/
│
├── gateway.js
├── service1/
│   └── service1.js
│
└── service2/
    └── service2.php
    
## Konfigurasi & Menjalankan Server
1. Jalankan Service 1 (Node.js)
- cd service1
- node service1.js

Berjalan di:
http://localhost:3001

2. Jalankan Service 2 (PHP)
- cd service2
- php -S localhost:3002 service2.php

Berjalan di:
http://localhost:3002

3. Jalankan API Gateway
node gateway.js

Berjalan di:
http://localhost:3000

## Mekanisme Routing Gateway
Endpoint Gateway	dialihkan ke
- /mahasiswa	Service 1 (Node.js)
- /produk	Service 2 (PHP)
  
## ENDPOINT API
1. Service 1: Mahasiswa (/mahasiswa)
   |Method|	  Endpoint	                  |      Deskripsi                  |
   |------|-------------------------------|---------------------------------|
   |GET	  |http../mahasiswa/api/mahasiswa |	 Ambil semua mahasiswa          |
   |GET	  |/mahasiswa/api/mahasiswa/	  |  Ambil mahasiswa berdasarkan ID |
   |POST  |/mahasiswa/api/mahasiswa	      |  Tambah mahasiswa               |
   |PUT	  |/mahasiswa/api/mahasiswa/	  |  Update mahasiswa               |
   |DELETE|/mahasiswa/api/mahasiswa/	  |  Hapus mahasiswa                |

3. Service 2: Produk (/produk)
   |Method|	  Endpoint	      |     Deskripsi               |
   |------|-------------------|-----------------------------|
   |GET	  |/produk/api/produk | Ambil semua produk          |
   |GET	  |/produk/api/produk/|	Ambil produk berdasarkan ID |
   |POST  |/produk/api/produk |	Tambah produk               |
   |PUT	  |/produk/api/produk/|	Update produk               |
   |DELETE|/produk/api/produk/|	Hapus produk                |
 
## Testing API
Gunakan:
1. Postman
2. Browser (GET)

Contoh:

GET http://localhost:3000/mahasiswa/api/mahasiswa
GET http://localhost:3000/produk/api/produk

⚠️ Notes Penting
1. Semua request harus melalui API Gateway (port 3000)
2. Service tidak diakses langsung oleh client
3. Data pada service masih bersifat sementara (in-memory / non-database)

## Fitur Utama
1. API Gateway sebagai single entry point
2. Routing request ke multi-service
3. Implementasi microservices sederhana
4. CRUD pada masing-masing service
5. Integrasi Node.js dan PHP dalam satu sistem

## Author
- Nama: Andito Dwi Wicaksono
- NIM: 2410511115
- Mata Kuliah: Pembangunan Perangkat Lunak Berorientasi Service (SE-2)
