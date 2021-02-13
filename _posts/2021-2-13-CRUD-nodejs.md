---
layout: post
title: CRUD dengan Node JS dan MySQL.
---

membuat crud sederhana dengan Node JS, Framework Express JS, template engine EJS dan Database SQL dmbs menggunakan mysql.

pertama install dulu package express js, template engine ejs dan mysql.

`npm install --save express ejs mysql`

selanjutnya buat database dengan nama `dbnodelogin`

buat table bernama `tbl_barang` dengan isi seperti berikut:

```SQL
CREATE TABLE `tbl_barang` (
  `id` int(11) NOT NULL,
  `kd_brg` int(11) NOT NULL,
  `nama` varchar(50) NOT NULL,
  `hrg_beli` int(11) NOT NULL,
  `hrg_jual` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

selanjutnya buat file `app.js` dan ketik kode seperti berikut:

```javascript
const { urlencoded } = require("body-parser");
const express = require("express");
const mysql = require("mysql");
const port = process.env.port || 3000;
const app = express();

// untuk mengakses folder public css
app.use(express.static("public"));
// untuk mengakses nilai form
app.use(express.urlencoded({ extended: false }));

// koneksi ke database
const connection = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "",
  database: "dbnodelogin",
});

connection.connect(function (err) {
  if (err) throw err;
});

// routing

// halaman index
app.get("/", (req, res) => {
  res.render("index.ejs");
});

// menampilkan list barang
app.get("/listbrg", (req, res) => {
  connection.query("SELECT * FROM tbl_barang", (error, results) => {
    res.render("listbrg.ejs", { tbl_barang: results });
  });
});

// menuju halaman add barang
app.get("/addbrg", (req, res) => {
  res.render("addbrg.ejs");
});

// add barang dari form
app.post("/createbrg", (req, res) => {
  var kd_brg = req.body.kd_barang;
  var nama = req.body.nama;
  var hrg_beli = req.body.hrg_beli;
  var hrg_jual = req.body.hrg_jual;
  connection.query(
    "INSERT INTO tbl_barang (kd_brg,nama,hrg_beli,hrg_jual) VALUES (?,?,?,?)",
    [kd_brg, nama, hrg_beli, hrg_jual],
    (error, results) => {
      res.redirect("/listbrg");
    }
  );
});

// hapus barang
app.post("/deletebrg/:id", (req, res) => {
  var id = req.params.id;
  connection.query(
    "DELETE FROM tbl_barang WHERE id=?",
    [id],
    (error, results) => {
      res.redirect("/listbrg");
    }
  );
});

// menampilkan edit barang
app.get("/editbrg/:id", (req, res) => {
  var id = req.params.id;
  connection.query(
    "SELECT * FROM tbl_barang WHERE id=?",
    [id],
    (error, results) => {
      res.render("editbrg.ejs", { tbl_barang: results[0] });
    }
  );
});

// update barang
app.post("/update/:id", (req, res) => {
  var kd_brg = req.body.kd_barang;
  var nama = req.body.nama;
  var hrg_beli = req.body.hrg_beli;
  var hrg_jual = req.body.hrg_jual;
  var id = req.params.id;
  connection.query(
    "UPDATE tbl_barang SET kd_brg=?, nama=?, hrg_beli=?, hrg_jual=? WHERE id=?",
    [kd_brg, nama, hrg_beli, hrg_jual, id],
    (error, results) => {
      res.redirect("/listbrg");
    }
  );
});

app.listen(port);
console.log("Server berjalan di port " + port);
```

untuk menampilkan ke halaman list barang, tambah, edit dan hapus barang, buat folder dengan nama `views` dan buat 4 file yaitu `index.ejs, addbrg.ejs, editbrg.ejs, listbrg.ejs`

untuk `index.ejs` kode seperti berikut:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Selamat Datang di Daftar Barang</title>
  </head>
  <body>
    <a href="/listbrg">Detail Barang</a>
  </body>
</html>
```

kode `addbrg.ejs` berikut:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Add Barang</title>
  </head>

  <body>
    <form action="/createbrg" method="post">
      <label>Kode Barang</label>
      <input type="text" name="kd_barang" required />
      <br />
      <label>Nama Barang</label>
      <input type="text" name="nama" required />
      <br />
      <label>Harga Beli</label>
      <input type="text" name="hrg_beli" required />
      <br />
      <label>Harga Jual</label>
      <input type="text" name="hrg_jual" required />
      <input type="submit" value="tambahkan" />
    </form>
  </body>
</html>
```

kode `editbrg.ejs` berikut:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Edit Barang</title>
  </head>

  <body>
    <form action="/update/<%= tbl_barang.id %>" method="post">
      <label>Kode Barang</label>
      <input type="text" name="kd_barang" value="<%= tbl_barang.kd_brg %>" />
      <br />
      <label>Nama Barang</label>
      <input type="text" name="nama" value="<%= tbl_barang.nama %>" />
      <br />
      <label>Harga Beli</label>
      <input type="text" name="hrg_beli" value="<%= tbl_barang.hrg_beli %>" />
      <br />
      <label>Harga Jual</label>
      <input type="text" name="hrg_jual" value="<%= tbl_barang.hrg_jual %>" />
      <input type="submit" value="Perbaharui" />
    </form>
  </body>
</html>
```

kode `listbrg.ejs` berikut:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>List Daftar Barang</title>
  </head>

  <body>
    <a href="/addbrg">Add Barang</a>
    <br />

    <table border="1px">
      <tr>
        <th>Kode Barang</th>
        <th>Nama Barang</th>
        <th>Harga Beli</th>
        <th>Harga Jual</th>
      </tr>
      <% tbl_barang.forEach((barang) => { %>
      <tr>
        <td><%= barang.kd_brg %></td>
        <td><%= barang.nama %></td>
        <td><%= barang.hrg_beli %></td>
        <td><%= barang.hrg_jual %></td>
        <td>
          <form action="/deletebrg/<%= barang.id %>" method="post">
            <input type="submit" value="Hapus" />
          </form>
        </td>
        <td><a href="/editbrg/<%= barang.id %>">Edit</a></td>
      </tr>
      <% }) %>
    </table>
  </body>
</html>
```

sekarang jalankan servernya dengan perintah `node app.js` dan akan berjalan pada `http://localhost:3000`

ini adalah tutorial CRUD Node Js Sederhana.

Terima kasih.

Anda bisa menemukan repo github saya di [Oliz Yusuf](https://github.com/olizyusuf) on GitHub.
