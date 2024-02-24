# Node-Running-Guide-Dusk-ITN
Node Running Guide Dusk ITN - Phase 2 (20 Feb - 15 Mar 2024)
<p align="center">
  <img height="auto" width="auto" src="https://dusk-cms.ams3.digitaloceanspaces.com/16_9_ITN_Set_Up_1eb7e84acb.png">
</p>

## Referensi

[Dokumen resmi](https://dusk.network/pages/incentivized-testnet#Wallet)

[Minta Faucet](https://docs.google.com/forms/d/e/1FAIpQLScxABRnszbBEaTZAIg2TwfJVIq0kRggy8QK2MRBTO7vuyP_Ug/viewform)

[Server discord](https://discord.gg/dusknetwork)

## Spesifikasi

### Persyaratan perangkat keras

| Komponen | Spesifikasi minimal |
|----------|---------------------|
|CPU|Intel Core 2|
|RAM|1 GB DDR4 RAM|
|Penyimpanan|20 GB HDD|

### Persyaratan perangkat lunak

| Komponen | Spesifikasi minimal |
|----------|---------------------|
|Sistem Operasi|Ubuntu 22|

| Komponen | Spesifikasi rekomendasi |
|----------|---------------------|
|Sistem Operasi|Ubuntu 22 atau lebih tinggi|

### BACA BAIK BAIK Jika Anda Menggunakan Ubuntu 18 - 20.04 (Instal Ini Agar Tidak Error) OPTIONAL

```
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb
```
```
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb
```
## 1. Instal CLI

```
sudo apt-get update
sudo apt install libssl-dev
sudo apt-get install -y tar wget curl
```
```
wget https://github.com/dusk-network/wallet-cli/releases/download/v0.13.0/ruskwallet0.13.0-linux-x64-libssl3.tar.gz
tar -xf ruskwallet0.13.0-linux-x64-libssl3.tar.gz
cd rusk-wallet0.13.0-linux-x64-libssl3
./rusk-wallet --state http://127.0.0.1:8080
```

## 2. Create Wallet

- Lalu Jika Muncul Tulisan `Create New Wallet` Klik Enter
- Masukan Password Bebas
- Masukan Password Lagi
- Copy dan Simpan Pharse Kalian
- Lalu Pilih `y` dan `Enter`
- Lalu Enter Lagi Nanti Muncul Address kalian Copy dan Simpan Juga
- Gunakan Arah Bawah Pada Keyboard Pc kalian
- Arahkan kan ke `Export Provisioner Key-Pair` dan `Enter`
- Lalu Isi Dengan Command di Bawah Ini, Tergantung Penempatan Directory anda Sendiri Kalo saya di Sini

```
/root/.dusk/rusk-wallet/
```
**Noted :** Seharusnya ada dua file sekarang, file .key dan file .cpk . Jaga kerahasiaan file .key , jangan bagikan dengan siapa pun. Kami akan membutuhkan file ini nanti untuk node kami. Anggap saja seperti kunci konsensus Anda, yang Anda gunakan untuk menandatangani transaksi.

.cpk adalah kunci publik. Kami membutuhkan yang ini untuk memberi Anda akses ke testnet.


- Balik ke VPS Arah Bawah Pilih `Back` dan `Enter`
- Arah Bawah Lagi Pilih `Exit` dan `Enter`
  
## 3. Instal Rusk-Node (update 23 Feb)
```
cd
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.4/itn-installer.sh | sudo sh
```
## 4. Buka Port 
```
sudo ufw allow 22
sudo ufw allow 8080
sudo ufw allow 9000:9005/udp
sudo ufw enable
```
## 5. Import Pharse Wallet
```
rusk-wallet restore
```
## 6. Paste Pharse Kalian (Pastikan Huruf Kecil Semua)
Masukan Password Bebas 2x
## 7. Jalankan Kode di Bawah
```
rusk-wallet export -d /opt/dusk/conf -n consensus.keys
```
Masukan password lagi 2x
```
sh /opt/dusk/bin/setup_consensus_pwd.sh
```
Masukan Password Lagi Samain Aja
## 8. Start Node
```
service rusk start
```
## Check log node
```
tail -f /var/log/rusk.log
```
## Check Wallet
```
rusk-wallet
```
- Pilih Acces Your Wallet dan Enter
- Masukan Password (Pastikan Address Kalian Sama Dengan Yang di Website)
- Gunakan Arah Atas Bawa Untuk Pindah Menu dan Enter Untuk Eksekusi


