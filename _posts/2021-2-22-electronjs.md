---
layout: post
title: Desktop App menggunakan Electron JS.
---

Dengan perkembangan teknologi sekarang, Electron JS menawarakan pembuatan aplikasi Desktop yang menggunakan web HTML, CSS, dan Javascript.
saya kali ini akan membagikan cara instalasi Electron JS.

clone dari repo electron.

`git clone https://github.com/electron/electron-quick-start`

buka folder yang telah di clone

`cd electron-quick-start`

selanjutnya install

`npm install`

setelah selesai tinggal dicoba saja.

`npm start`

voilaaa berhasil dibuka dengan hasil seperti ini.\
![electronjs]({{ site.baseurl }}/images/electron-quick.png)

sekarang saya akan mencoba membuat 2 halaman dengan menambahkan `about.html` dan mengedit file `index.html`

![electronjs2]({{ site.baseurl }}/images/vscode.png)

isi kode pada `about.html` sebagai berikut:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <!-- https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP -->
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self'; script-src 'self'"
    />
    <meta
      http-equiv="X-Content-Security-Policy"
      content="default-src 'self'; script-src 'self'"
    />
    <title>Home</title>
  </head>

  <body>
    <h1>Selamat Datang.</h1>

    <a href="about.html">About</a>

    <p>Aplikasi ini dibuat menggunakan electron js.</p>

    <!-- You can also require other files to run in this process -->
    <script src="./renderer.js"></script>
  </body>
</html>
```

dan pada `about.html` sebagai berikut:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <!-- https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP -->
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self'; script-src 'self'"
    />
    <meta
      http-equiv="X-Content-Security-Policy"
      content="default-src 'self'; script-src 'self'"
    />
    <title>About</title>
  </head>

  <body>
    <h1>Ini Adalah Halaman About</h1>

    <a href="index.html">Kembali ke Halaman Home.</a>

    <!-- You can also require other files to run in this process -->
    <script src="./renderer.js"></script>
  </body>
</html>
```

hasilnya akan seperti ini

![electronjs3]({{ site.baseurl }}/images/appelectron.gif)

teman-teman dapat mengembangkannya lagi dan ini memudahkan kita sebagai developer yang senang menggunakan bahasa pemrograman
javascript.

Anda bisa menemukan repo github saya di [Oliz Yusuf](https://github.com/olizyusuf) on GitHub.
