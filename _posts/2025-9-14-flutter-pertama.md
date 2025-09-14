---
layout: post
title: Membuat Aplikasi Flutter
---

Flutter adalah framework cross platform yang populer untuk mengembangkan aplikasi android maupun ios, bahkan sudah bisa membuat web app ataupun desktop app, disini saya akan menjelaskan bagaimana cara membuat aplikasi dengan Flutter, tentu saja sebelum mengikuti ini anda harus sudah menginstall dulu Flutter SDK dan penunjangnya seperti text editor vscode yang akan saya gunakan juga.

## Membuat Proyek Baru

buka cmd/terminal lalu letakkan di folder yang anda akan buat untuk meletakan project aplikasinya.
ketikkan diterminal

`flutter create myapp`

dan tunggu sampai berhasil, nama project yg saya buat yaitu myapp jika sudah berhasil lalu

`cd myapp`

setelah sudah difolder myapp buka dengan text editor.

buka dilokasi `lib/main.dart` , ubah menjadi seperti dibawah ini.
{% highlight dart %}

void main() {
String helloWorld = "Hello World";
print(helloWorld);
}

{% endhighlight dart %}

Selanjutnya kalian bisa langsung build app ke _real devices_ atau _emulator_, tunggu sampai aplikasi muncul.

Flutter mempunyai Kelebihan yaitu fitur _hot reload_, memudahkan developer melihat langsung perubahan yang ditampilan antarmuka setelah melakukan perubahan pada kode.

Sekian.
