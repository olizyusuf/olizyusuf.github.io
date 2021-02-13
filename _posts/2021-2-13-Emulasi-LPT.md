---
layout: post
title: Panduan Emulasi LPT Printer pada Port USB.
---

Halo semua, kali ini saya akan berbagi pengalaman perihal port LPT yang notabene masih dipakai pada program lama yang membutuhkan direct print ke LPT tetapi menggunakan printer yang memakai port USB. tutorial ini saya sudah implementasikan pada printer STAR receipt printer dengan OS Windows 7, untuk printer lain mungkin bisa diimplementasikan. berikut panduannya:

1. Instal driver Printer STAR menggunakan port USB dan dipastikan test print dengan baik.
2. Selanjutnya printer di Sharing dengan nama `printer`.
3. Instal driver printer STAR melalui Add Printer secara manual dan gunakan pilihan port `LPT` dan ubah menjadi Default printer.
4. Buat loop back adapter melalui `device manager` yaitu `add new hardware -> Advance List -> Network Adapters -> Microsoft -> Microsoft Loopback Adapter` , dan cek di network devices jika sudah muncul berarti sudah berhasil membuat loop back adapter.
5. Setting IP pada loop back adapter dengan IP `192.168.77.1/24`.
6. Buat mapping printer dengan perintah `NET USE LPT1:\\IP_LOOPING\NAMA_SHARING_PRINTER /PERSISTENT:YES`

\*\*\* contoh:
`NET USE LPT1: \\192.168.77.1\PRINTER /PERSISTENT:YES`

---

Perintah mapping ini sebaiknya ditest dahulu pada command promt, apabila command tersebut success / tidak ada error, maka dilakukan test print komunikasi `DIR>LPT1` menggunakan command prompt, apabila sukses maka perintah maping
diatas dibuatkan batch file. kemudiakan diletakan di startup tujuan agar setiap restart printer tersebut tereksekusi.

Anda bisa menemukan repo github saya di [Oliz Yusuf](https://github.com/olizyusuf) on GitHub.
