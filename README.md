# nodejs-auth-jwt
Authentication JWT Node.js

> https://blog.cacan.id/authentication-jwt-node-js

![000](https://user-images.githubusercontent.com/51890752/99249527-d87ab000-283c-11eb-9a50-d6736746f6e2.jpg)


# Cara Penggunaan:

## Clone dari GitHub:
    git clone https://github.com/blogcacanid/nodejs-auth-jwt.git

## Lalu masuk ke direktori project:
    cd nodejs-auth-jwt

## Database
Buat database baru dengan nama nodejs_auth_jwt
Dari command prompt ketikkan perintah berikut:

    mysql -uroot -p
    CREATE DATABASE nodejs_auth_jwt;

Selanjutnya buat table users.
Dari command prompt ketikkan perintah berikut:

		USE nodejs_auth_jwt;

		CREATE TABLE `users` (
			`id` int(11) NOT NULL AUTO_INCREMENT,
			`username` varchar(255) DEFAULT NULL,
			`email` varchar(255) DEFAULT NULL,
			`password` varchar(255) DEFAULT NULL,
			`createdAt` datetime NOT NULL,
			`updatedAt` datetime NOT NULL,
			PRIMARY KEY (`id`)
		) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

### Configure Database
Selanjutnya buka file .env folder root project kemudian edit bagian DB menjadi seperti berikut:
Selanjutnya buka file db.config.js pada direktori app/config kemudian edit konfigurasi database seperti berikut: (Silahkan disesuaikan)

		module.exports = {
			HOST: "localhost",
			USER: "root",
			PASSWORD: "j.fUjHyL",
			DB: "nodejs_auth_jwt",
			dialect: "mysql",
			pool: {
				max: 5,
				min: 0,
				acquire: 30000,
				idle: 10000
			}
		};


## Testing
Jalankan Node JS dengan menggunakan perintah berikut:

    node server.js


### Testing via Postman
Selanjutnya kita akan testing menggunakan Postman.

#### Register
Pertama-tama kita daftarkan user baru terlebih dahulu agar kita bisa melakukan login.
Buka postman lalu pilih method POST kemudian ketikkkan URL 

    http://localhost:9090/api/auth/register

Kemudian pilih tab Body. Lalu pada radiobox pilih raw dan typenya pilih JSON. 
Selanjutnya pada bagian textbox inputkan data registrasinya seperti berikut:

    {
		"username": "rony",
		"email": "rony@email.com",
		"password": "rahasia"
    }
    
Selanjutnya klik tombol Send

![001](https://user-images.githubusercontent.com/51890752/99249377-9cdfe600-283c-11eb-8530-3f2035be846b.jpg)



#### Login
Setelah registrasi berhasil selanjutnya kita coba untuk login dengan user yang sudah kita registrasikan tersebut.
Buka postman lalu pilih method POST kemudian ketikkkan URL http://localhost:9090/api/auth/login
Kemudian pilih tab Body. Lalu pada radiobox pilih raw raw dan typenya pilih JSON. Selanjutnya pada bagian textbox inputkan data email dan password untuk login:

    {
		"username": "rony",
		"password": "rahasia"
    }

Selanjutnya klik tombol Send

![002](https://user-images.githubusercontent.com/51890752/99249556-e5979f00-283c-11eb-84dc-57a37d57aa36.jpg)


Jika login berhasil, maka kita akan mendapatkan access token. 


