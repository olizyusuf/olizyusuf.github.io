---
layout: post
title: Kalkulator Sederhana dengan JAVA.
---

Berikut pembuatan kalkulator sederhana menggunakan Java. kode dibawah ini sangat sederhana dengan operator logika if else if else.

Langkah awal membuat new java package.
Setelah itu buat Java class dengan nama Kalkulator
Sebenarnya jika ingin membuat kalkulator sederhana ini sangat mudah jika sudah memahami dasar-dasar pemrograman java. biasanya Kalkulator sederhana ini masuk dalam tugas makul dari dosen.
Dengan begitu tinggal ketikan kode dibawah ini :

```java
import java.util.Scanner;

/**
 *
 * @author oliz
 */
public class Kalkulator {
    public static void main(String[] args) {

        // deklarasi
        int nilai1, nilai2, hasil;
        String operator;

        // input
        Scanner keyboard = new Scanner(System.in);

        // proses
        System.out.println("=== Kalkulator Sederhana ===");
        System.out.print("Masukan nilai-1: ");
        nilai1 = keyboard.nextInt();
        System.out.print("pilih operator +, -, x, :, %: ");
        operator = keyboard.next();
        System.out.print("Masukan nilai-2: ");
        nilai2 = keyboard.nextInt();

        // menghitung nilai sesuai operator aritmatika
        if ( operator.equalsIgnoreCase("+") ) {
            hasil = nilai1 + nilai2;
        } else if ( operator.equalsIgnoreCase("-") ) {
            hasil = nilai1 - nilai2;
        } else if ( operator.equalsIgnoreCase("x") ) {
            hasil = nilai1 * nilai2;
        } else if ( operator.equalsIgnoreCase(":") ) {
            hasil = nilai1 / nilai2;
        } else {
            hasil = nilai1 % nilai2;
        }

        System.out.println("Hasil: " + hasil);
    }
}
```

Penjelasannya membuat deklarasi int nilai1, nilai2, hasil; dan String operator; lalu proses input menggunakan import java.util.Scanner; dengan membuat input deklarasi Scanner keyboard = new Scanner(System.in); . dengan begitu selanjut menangkap input dengan proses keyboard.nextInt(); untuk nilai int dan keyboard.next(); untuk nilai string. selanjutnya proses menghitung sesuai operator aritmatika yang di input bentuk string dengan mengecek melalui proses operator.equalsIgnoreCase("+") yaitu mengecek tanpa mengecek camelcasenya. setelah itu proses output akan menampikan hasil yang telah diinput tadi.

Setelah selesai dan pastikan penulisan dengan benar maka eksekusi kode tersebut, jika menggunakan netbeans tinggal pencet shift + f6 atau klik kanan run. Maka hasil dari eksekusi tersebut seperti berikut :

![kalkualtor]({{ site.baseurl }}/images/kalkulatorjava.png)
