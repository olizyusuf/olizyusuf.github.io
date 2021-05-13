---
layout: post
title: Backend dengan framework Hapi
---

Buat folder dengan nama hapi-web-server dahulu

`mkdir hapi-web-server`

buka folder yang sudah dibuat

`cd hapi-web-server`

selanjutnya yaitu inisialisasi `npm init --y` supaya langsung saja sy tambahkan --y

jika sudah maka kita lanjut membuat 2 file yaitu `server.js` dan `routes.js`

buka file `package.json` setting seperti berikut:

```
{
  "name": "hapi-web-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "node server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "@hapi/hapi": "^20.1.3"
  }
}
```
jika sudah kita coba isi `server.js` dengan 
`console.log('halo dunia');`
dan di terminal jalankan `npm run start`
jika tidak error maka sudah siap kita setup.
edit `server.js` dan isi dengan:
```
const Hapi = require("@hapi/hapi");
const routes = require("./routes");

const init = async () => {
  const server = Hapi.server({
    port: 5000,
    host: "localhost",
  });

  server.route(routes);

  await server.start();
  console.log(`Server berjalan pada ${server.info.uri}`);
};

init();

```
dan isi juga `routes.js` dengan:
```
const routes = [
  {
    method: "GET",
    path: "/",
    handler: (request, h) => {
      return "Homepage";
    },
  },
  {
    method: "*",
    path: "/",
    handler: (request, h) => {
      return "Halaman tidak dapat diakses dengan method tersebut";
    },
  },
  {
    method: "GET",
    path: "/about",
    handler: (request, h) => {
      return "About page";
    },
  },
  {
    method: "*",
    path: "/about",
    handler: (request, h) => {
      return "Halaman tidak dapat diakses dengan method tersebut";
    },
  },
  {
    method: "GET",
    path: "/hello/{name?}",
    handler: (request, h) => {
      const { name = "stranger" } = request.params;
      const { lang } = request.query;
      if (lang === "id") {
        return `Hai, ${name}!`;
      }
      return `Hello, ${name}!`;
    },
  },
  {
    method: "*",
    path: "/{any*}",
    handler: (request, h) => {
      return "Halaman tidak ditemukan";
    },
  },
];

module.exports = routes;

```

untuk mengetestnya tinggal jalankan `npm run start` di terminal dan kita test menggunakan perintah berikut.
```
curl -X GET http://localhost:5000/

```
jika output `homepage` berarti berhasil sudah pembuatan webserver menggunakan framework hapi.


Anda bisa menemukan repo github saya di [Oliz Yusuf](https://github.com/olizyusuf) on GitHub.
