---
layout: post
title: Install XAMPP Linux
---

Setelah migrasi dari windows ke linux, tentunya perlu sekalian
instal keperluan developer php, sekalian buat tutorialnya agar kedepan habis instal ulang bisa tinggal buka aja.

### 1. Persiapan update dan Web Browser

![chrome]({{ site.baseurl }}/images/xampp/01.linux.png)

Setelah install os linux kita update "apt"

`sudo apt-get update`

Lanjut kita butuh browser chrome kalian bisa download google chrome dulu berbentuk file **_.deb_**

![chrome]({{ site.baseurl }}/images/xampp/02.chrome.png)

via terminal buka ke ke folder download kalian lanjut lakukan perintah instal.

`sudo dpkg -i google-chrome-stable_current_amd64.deb``

### 2. Text Editor

kita membutuhkan text-editor, bisa download VScode berbentu file **_.deb_** , disini kalian bisa menggunakan text editor lainnya seperti sublime atau vim.

![vscode]({{ site.baseurl }}/images/xampp/03.vscode.png)

via terminal buka ke ke folder download kalian lanjut lakukan perintah instal.

`sudo dpkg -i code_1.85.1-1702462158_amd64`

\*\* _nama file sesuaikan dengan versi yang kalian download._

### 3. Instal XAMPP.

Selanjutnya kita download dulu XAMPP dari website officialnya.

![xampp]({{ site.baseurl }}/images/xampp/05.xampp.png)

lakukan perintah instal di terminal.

`sudo ./xampp-linux-x64-7.4.33-0-installer.run`

\*\* _nama file sesuaikan dengan versi yang kalian download._

ikuti petunjuknya sampai selesai.
lakukan running apache dan mysql dengan cara

`sudo /opt/lampp/lampp startapache`
`sudo /opt/lampp/lampp startmysql`

buka browser dan test dengan url

`http://localhost`

![apachemysql]({{ site.baseurl }}/images/xampp/06.apachexamp.png)

Selanjutnya kita bisa lakukan export path agar php dan mysql bisa kita akses lewat terminal.

`sudo nano \.bashrc`

lakukan menambahan dibawah sendiri

`export PATH="/opt/lampp/bin:$PATH"`

lanjut kita export path yang sudah ditambahkan ke **_.bashrc_**

`source \.bashrc`

jika sudah di export bisa kita pastikan dengan perintah

`echo $PATH`

jika sudah ada **_/opt/lampp/bin_** berarti path sudah berhasil ditambah kalian bisa melakukan test juga dengan.

`php -v`

Untuk memeriksa versi php, jika berhasil akan tertulis seperti ini.
{% highlight terminal %}
PHP 7.4.33 (cli) (built: Nov 22 2022 11:36:42) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
{% endhighlight terminal %}

Kalian bisa lanjut untuk develop aplikasi web yang ingin kalian buat.

---

Anda bisa menemukan repo github saya [disini](https://github.com/olizyusuf) (olizyusuf) on GitHub.
