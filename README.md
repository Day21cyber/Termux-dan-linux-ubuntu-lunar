# Termux dan Linux Ubuntu Lunar
![gambar termux](https://github.com/Day21cyber/Termux-dan-linux-ubuntu-lunar/blob/main/Screenshot_20240308_142819.jpg)
<html>
  <body>
<h1>Pengenalan</h1>
<p>Termux adalah aplikasi terminal emulator dan lingkungan Linux untuk Android yang bekerja langsung tanpa rooting atau pengaturan khusus. Ini menyediakan akses ke shell Linux dan berbagai paket yang dapat diinstal melalui manajer paket APT.
Ubuntu Lunar adalah salah satu distro Linux yang berbasis Ubuntu. Meskipun belum banyak informasi tentang Ubuntu Lunar, kita bisa membahas Ubuntu sebagai dasarnya.</p>
<h1>Termux: Terminal Emulator di Android</h1>
<p>Termux mengubah perangkat Android menjadi workstation portabel, memberikan Anda akses ke shell bash, serta berbagai utilitas dan bahasa pemrograman yang biasanya tersedia di sistem berbasis UNIX. Anda dapat menggunakan Termux untuk:</p>
    <ul>
<li>•	Mengedit file dengan nano dan vim.</li>
<li>•	Mengakses server melalui SSH.</li>
<li>•	Menggunakan git untuk mengelola proyek Anda.</li>
<li>•	Menjalankan teks berbasis game dengan frotz.</li>
    </ul>
  <h1>Ubuntu Lunar: Distro Linux yang Berbasis Ubuntu</h1>
<p>Ubuntu adalah salah satu distro Linux yang paling populer dan mudah digunakan. Ubuntu menawarkan stabilitas dan dukungan jangka panjang (LTS), menjadikannya pilihan yang baik untuk pengguna baru dan perusahaan.
Ubuntu Lunar, sebagai distro yang berbasis Ubuntu, kemungkinan akan menawarkan fitur dan kestabilan yang sama dengan Ubuntu, dengan beberapa penyesuaian dan peningkatan khusus.</p>
<h2>Kesimpulan</h2>
<p>Baik Termux maupun Ubuntu (dan varian seperti Ubuntu Lunar) menawarkan alat yang kuat untuk penggunaan sehari-hari dan pengembangan. Dengan Termux, Anda dapat membawa kekuatan Linux ke perangkat Android Anda, sementara Ubuntu dan varian-varian seperti Ubuntu Lunar menawarkan lingkungan desktop yang stabil dan user-friendly.</p>
<p>Harap dicatat bahwa informasi ini mungkin berubah dan selalu disarankan untuk memeriksa situs web resmi atau sumber tepercaya untuk informasi terkini.</p>
  </body>
</html>

---

# Panduan Memasang Aplikasi Termux

Termux adalah aplikasi emulator terminal yang memungkinkan pengguna untuk mengakses lingkungan Linux lengkap di perangkat Android mereka. Dengan Termux, pengguna dapat menginstal dan menjalankan berbagai perintah dan paket Linux di ponsel pintar mereka. Berikut adalah langkah-langkah untuk memasang aplikasi Termux:

## Langkah 1: Unduh Aplikasi Termux

Langkah pertama adalah mengunduh dan menginstal aplikasi Termux dari sumber yang dipercayai. Anda dapat mengunduhnya dari [F-Droid](https://f-droid.org/packages/com.termux/) atau [Google Play Store](https://play.google.com/store/apps/details?id=com.termux&hl=en&gl=US).

## Langkah 2: Instalasi Termux dari F-Droid

1. Buka aplikasi F-Droid di perangkat Anda.
2. Cari "Termux" menggunakan fitur pencarian.
3. Ketika aplikasi Termux muncul, ketuk ikon unduhan di sebelah kanan untuk mengunduh dan memasangnya.

## Langkah 3: Mulai Menggunakan Termux

Setelah aplikasi Termux terinstal, Anda dapat membuka aplikasi tersebut dan mulai menjalankan perintah-perintah Linux seperti yang Anda lakukan di terminal pada komputer.

Dengan mengikuti langkah-langkah di atas, Anda dapat dengan mudah memasang aplikasi Termux dan mulai menjelajahi dunia Linux di perangkat Android Anda.

## Referensi:
- [Aplikasi Termux di F-Droid](https://f-droid.org/packages/com.termux/)

Sekarang Anda sudah siap untuk menjalankan Termux dan mulai menjelajahi dunia Linux di perangkat Android Anda!

---
Catatan: Pastikan untuk memperbarui dan memasang paket-paket yang diperlukan dengan perintah `apt update` dan `apt upgrade` setelah menginstal Termux.

---

# Penginstalan  Termux dan Ubuntu dekstop

## Langkah 1: Persiapan dan Pengaturan Awal
```bash
pkg update -y
termux-setup-storage 
pkg install git -y
pkg install curl -y
pkg install wget -y
pkg install proot-distro -y
proot-distro install ubuntu 
proot-distro login ubuntu 
exit
echo "proot-distro login ubuntu --bind /dev/null:/proc/sys/kernel/cap_last_cap" >> $PREFIX/bin/ubuntu
chmod +x $PREFIX/bin/ubuntu
```

## Langkah 2: Konfigurasi Ubuntu
```bash
ubuntu
apt update
apt install sudo -y
apt install adduser -y

## Langkah 3: Instalasi Desktop Environment dan Aplikasi
```bash
apt update && apt dist-upgrade -y ; apt install xfce4 xfce4-terminal xfce4-whiskermenu-plugin ubuntu-wallpapers dbus-x11 sudo plank git gedit dconf-editor yaru-theme-gtk yaru-theme-icon -y ; git clone https://github.com/adi1090x/rofi ; cd rofi ; ./setup.sh ; cd ; ln -s /data/data/com.termux/files/home/storage
```
## Setelah itu paste :
```bash
nano /etc/sudoers
```
Tambahkan yang ada tulisan `# User privilege specification` di bawah `root`:
```
Nama_kamu    ALL=(ALL:ALL) ALL
```
Tekan `Ctrl s` dan `x`
```bash
adduser Nama_kamu
su - Nama_kamu 
whoami
sudo whoami
```

## konfigurasi desktop
```bash
mkdir ~/.vnc
nano ~/.vnc/xstartup
```
## paste ini
```bash
#!/bin/bash

export XDG_CURRENT_DESKTOP="XFCE"
startxfce4 &
```
## Recommended packages:
```bash
  printer-driver-braille appmenu-qt jayatana ubuntu-system-service
  systemd-services
```

## Instalasi Browser Web (Pilih Salah Satu)
### Chromium
```bash
sudo apt install gnupg ; echo "deb http://ftp.debian.org/debian stable main contrib non-free" >> /etc/apt/sources.list ; sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 648ACFD622F3D138 ; sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 0E98404D386FA1D9 ; sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 605C66F00D6C9793 ; sudo apt update ; sudo apt install chromium
```
### Firefox
```bash
sudo apt install gnupg ; echo "deb http://ftp.debian.org/debian stable main contrib non-free" >> /etc/apt/sources.list ; sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 648ACFD622F3D138 ; sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 0E98404D386FA1D9 ; sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 605C66F00D6C9793 ; sudo apt update ; sudo apt install firefox-esr
```

## Langkah 4: Pengaturan VNC
Keluar dari repositori ubuntu dengan mengetik `exit` paste kode dibawah ini .
```bash
echo "DISPLAY=:1 xfce4-session" > /usr/local/bin/startserver ; chmod +x /usr/local/bin/startserver
pkg install x11-repo ; pkg install xorg-xhost tigervnc -y ; echo "vncserver -geometry 1600x700 -listen tcp :1 ; DISPLAY=:1 xhost +" > ../usr/bin/connectvnc ; chmod +x ../usr/bin/connectvnc
```

## Menghubungkan Ke SERVER VNC
Setelah memasukkan semua perintah di atas, untuk terhubung ke vncserver, di Termux ketikkan perintah di bawah ini.
```bash
connectvnc
```
Setelah itu beralih ke ubuntu dan ketik perintah di bawah ini untuk terhubung ke vnc host
```bash
startserver
```

## Langkah 5: Instalasi Aplikasi Tambahan (Opsional)
```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install vlc -y
sudo apt install kdenlive -y
sudo apt install gimp -y
sudo apt install libreoffice -y
sudo apt install lmms -y
sudo apt install audacity -y
```

Dengan mengikuti langkah-langkah di atas, Anda dapat dengan mudah menginstal dan mengkonfigurasi aplikasi Termux dan Ubuntu di perangkat Android Anda.


hubungi kami [grub wa]
Buka tautan ini untuk bergabung ke grup WhatsApp saya: (https://chat.whatsapp.com/JDy9ito5fQ09QajwJJXHsZ)
