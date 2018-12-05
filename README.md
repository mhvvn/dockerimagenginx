## Persiapan 
- buat direktori khusus untuk membuat image ini, contoh: dockerimagenginx
- hubungkan direktori tersebut ke github anda
- Setelah point II selesai, push source code ke github anda.

## Buatlah docker image dengan menggunakan Dockerfile
Mengikuti kriteria berikut:
1. menggunakan base image nginx:latest
2. menjalankan perintah : apt-get update -q && apt-get dist-upgrade -y && apt-get clean && apt-get autoclean && apt-get install openssl -y
3. environment setup: ENV WWW_PATH /usr/share/www/html
4. menjalankan perintah: mkdir -p $WWW_PATH && chown nginx:nginx $WWW_PATH
5. Memiliki opsi: ARG PASSWORD=pass
6. Menjalankan perintah: printf "user:$(openssl passwd -1 $PASSWORD)\n" >> $WWW_PATH/.htpasswd
7. Menjalankan perintah hapus konfigurasi default nginx, yaitu: rm /etc/nginx/conf.d/default.conf
8. Menambahkan file config nginx ke dalam docker image dengan perintah: COPY etc/nginx/conf.d/main.conf /etc/nginx/conf.d/
9. Mengkopi file-file dari direktori lokal ke docker image, dengan perintah: COPY usr/share/www/html/ /usr/share/www/html/

