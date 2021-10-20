---
name: Membuat Route Api Seperti Next.js Dengan Vite.js Dan Vue.js
thumbnail: https://i.ibb.co/0KDP2Hg/thumbnail.jpg
date: 2021-10-20
description: Sekarang kamu bisa menggunakan route API di aplikasi Vue JS seperti hal nya yang ada di Next JS loh, penasaran? baca dulu sini :D
tags: ['vite', 'vue', 'javascript']
---

Jika sudah ada yang pernah pakai [Next JS](https://nextjs.org/), pasti sudah tau dong fitur route API yang dimiliki oleh Next JS, disana kamu bisa membuat backend API untuk aplikasi frontend kamu, nantinya API itu bisa kamu akses dengan cara menambahkan route `/api`. Nah sekarang Saya akan membagi tahu cara membuat fitur tersebut dengan menggunakan [Vue.js 3](https://v3.vuejs.org/) dengan bantuan [Vite.js 2](https://vitejs.dev/) dan plugin [Vite Plugin Mix](https://github.com/egoist/vite-plugin-mix) yang dibuat oleh [Egoist](https://github.com/egoist). Simak selengkapnya disini

<h1>Daftar isi</h1>

[[toc]]

# Instalasi

Hal pertama yang dilakukan adalah melakukan penginstalan aplikasi vite + vue di terminal console kalian masing-masing. Untuk cara penginstalannya tidak akan saya jelaskan karena caranya bisa lihat di dokumentasi vite.js nya langsung, bisa klik [disini](https://vitejs.dev/guide/#scaffolding-your-first-vite-project). Jika sudah instal semua projek vite tersebut, sekarang saat nya menginstall plugin vite-plugin-mix di terminal console kalian, caranya bisa dengan menjalankan perintah dibawah ini

```bash
npm i vite-plugin-mix --save-dev
```

# Mulai mengkoding

---

## Daftarkan plugin di vite.config.js

Hal pertama yang dilakukan adalah memasang plugin ini ke file yang bernama `vite.config.js`, buka file tersebut dan tambahkan beberapa kode, kode-nya bisa dilihat dibawah ini

```js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import mix from 'vite-plugin-mix'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue(),
    mix({
      handler: './handler.js'
    })
  ]
})

```

Berikut akan saya jelaskan apa maksud dari kode diatas. Pertama-tama kita import lib `vite-plugin-mix` tersebut setelah itu, masukkan function `mix` tersebut kedalam array `plugins` yang ada didalam option `defineConfig` dari vite, setelah itu tambahkan option object didalam function `mix` yang bernama `handler` yang dimana object tersebut memiliki nilai yaitu nama file js dari handler tersebut, disini saya menamakan `handler.js`.

## Membuat API

Setelah mendaftarkan plugin tersebut didalam file `vite.config.js`, selanjutnya kita akan membuat satu file di root folder, dengan nama `handler.js` sesuai dengan yang sudah didaftarkan sebelumnya. Setelah dibuat, saatnya mulai mengkoding untuk membuat route API nya hehe.

```js
export const handler = (req, res, next) => {
  if (req.path === '/hello') {
    return res.end('hai');
  }
  next();
};
```

Berikut akan saya jelaskan maksud dari script diatas, script diatas merupakan script untuk membuat route API nya dengan endpoint yang bernama `/hello` yang dimana ketika nanti endpoint tersebut dipanggil, akan mengembalikan sebuah response dan response nya itu adalah `hai`, yang pertama dilakukan adalah membuat sebuah function yang bernama handler(btw disini nama function-nya bebas ya bisa selain handler seperti dicontoh) yang dimana harus diexport. Setelah itu kita bisa membuat enpointnya, caranya bisa dilakukan dengan cara membuat pengujian jika path url itu adalah `/hello` maka akan mengembalikan sebuah response berupa text `hai`.

## Eksekusi API

Setelah sudah membuat API-nya di file `handler.js`, saatnya kita mengeksekusi API-nya, cara yang pertama itu adalah, sebagai berikut:

1. Nyalakan server vite terlebih dahulu, bisa dengan cara

```bash
npm run dev # Akan membuat server localhost dengan port 3000 secara default
```

atau

```bash
npx vite --port=4000 # Akan membuat server localhost dengan port 4000
```

2. Jalankan endpoint
Setelah server vite sudah berjalan, saatnya kita memanggil endpoint tersebut, memanggilnya bisa di browser kalian atau di postman dan sejenisnya dengan cara hanya menambahkan endpoint `/hello` setelah base url kalian seperti berikut

<img 
  src="https://i.ibb.co/0hdQ16S/image-2021-10-20-03-08-55.png" 
  alt="gambar-hasil-route-api" 
  class="rounded w-full shadow" 
  loading="lazy" 
/>

> Disini saya menggunakan [Stackblitz](https://stackblitz.com/), saya menggunakan ini agar saya tidak perlu lagi menginstall projek ini di laptop saya.

Nah sudah berhasil kan? sekarang kalian sudah bisa menggunakan route API seperti di Next.js di aplikasi Vue.js kalian dengan bantuan vite dan vite-plugin-mix. Oh ya, selain itu kalian bisa menggabungkannya dengan Express.js dan sejenisnya, selengkapnya bisa cek [disini](https://github.com/egoist/vite-plugin-mix).

# Kesimpulan

[Vite.js](https://vitejs.dev/) merupakan sebuah *frontend tooling* yang bisa membantu para developer untuk mengembangkan suatu website dengan lebih cepat lagi salah satunya pada saat mengembangkan website dengan menggunakan framework Vue.js. Vite.js juga memiliki banyak sekali ekosistem mengingat ini sebuah projek open source dan salah satunya adalah [vite-plugin-mix](https://github.com/egoist/vite-plugin-mix) yang dimana kalian bisa menambahkan sebuah backend API di aplikasi Vite.js kalian, atau dengan kata lain, jika kalian sudah pernah menggunakan [Next.js](https://nextjs.org/) pastinya tidak akan asing dengan istilah *route API*, dengan menggunakan plugin ini, kalian bisa menambahkan *route API* sebagaimana mestinya yang ada di Next.js.

# Penutup

Wah akhirnya sudah dipenghujung tulisan saya :D, sekali lagi terima kasih buat kalian yang sudah membaca blog saya kali ini dari awal sampai akhir, semoga bermanfaat buat kalian semua serta mohon maaf kalau ada yang kurang dan kesalahan kata😁. Oh ya akhir kata, sampai jumpa lagi diblog saya selanjutnya ya :D

> Oh ya hampir lupa kalau terima kasih harus pakai emoji ini 🙏 ya kalau zaman sekarang.
