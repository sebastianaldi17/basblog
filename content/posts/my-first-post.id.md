---
title: "Postingan Pertama, Website Ketiga"
date: 2022-04-03T11:30:03+07:00
# weight: 1
# aliases: ["/first"]
tags: ["kehidupan"]
author: "Saya"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Membuat website pribadi lagi, untuk ketiga kalinya."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "https://images.unsplash.com/photo-1555066931-4365d14bab8c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80" # image path/url
    alt: "Generic coding picture" # alt text
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
---
# Website ketiga?
Ya, ini kali ketiga saya membuat website pribadi. Pertama kali menggunakan `HTML`, `Bootstrap`, dan `Javascript` biasa, kemudian menerbitkan ke Github Pages. Kedua kalinya menggunakan `React.js` dengan `Material-UI`, yang dapat dilihat [di sini](https://github.com/sebastianaldi17/React-Personal-Site), lalu memakai `netlify` untuk hosting halaman statis, dan itu bekerja dengan cukup baik sampai saya memutuskan untuk menghapus website web karena beberapa alasan:

- Saya mendapat pekerjaan sebagai insinyur perangkat lunak (Software Engineer), jadi saya merasa tidak perlu terlalu banyak mengiklankan diri.
- Saya ingin membuat blog, tetapi pada saat itu saya tidak tahu caranya karena saya ingin menyimpan folder yang penuh dengan file `markdown` yang berfungsi sebagai konten blog, tetapi saya tidak dapat menjalankannya tanpa backend melalui folder yang berisi beberapa file `markdown`.

Setelah seorang rekan kerja memutuskan untuk meninggalkan pekerjaan mereka saat ini, saya memutuskan bahwa saya ingin mulai lebih terbuka ke tawaran. Solusi yang saya putuskan untuk digunakan adalah menggunakan [hugo](https://gohugo.io/) untuk membuat file `HTML` statis dari file `markdown`. Saya menggunakan `hugo` karena `hugo` menggunakan `Go`, yang sudah diinstal di laptop saya (dibandingkan dengan menggunakan `jekyll` yang membutuhkan `Ruby` diinstal, tetapi setelah dipikir-pikir ini mungkin jauh lebih mudah karena Github pages mendukungnya).

`Hugo` sama sekali tidak ingin bermain-main dengan halaman Github. Saya mencoba menggunakan metode `github-actions` (membuat file statis di cabang terpisah dan halaman Github menunjukkannya), tetapi setiap posting mengembalikan 404 not found (dari halaman Github, bukan dari `hugo` itu sendiri). Di sisi lain, `netlify` berjalan dengan baik tanpa banyak masalah, itulah sebabnya saya menggunakannya.

# Siapa aku?
Saya seorang Software Engineer (Backend) lulusan Universitas Pelita Harapan pada tahun 2021, dan saat ini bekerja di Tokopedia. Beberapa hobi saya adalah:
- Rhythm game (arcade dan non arcade, misalnya maimai, sound voltex, osu!)
- Keyboard mekanik
- Perlengkapan audio

# Keadaan saat penulisan
Pada saat penulisan ini, saya baru saja selesai menjalani endoskopi karena saya cenderung muntah setelah makan atau minum apa pun. Masalah pencernaan saya dimulai pada tahun 2018, ketika saya terus melewatkan makan malam karena menjadi mahasiswa, guru les, dan panitia acara pada saat yang bersamaan. Dokter mendiagnosis saya dengan [esofagitis](https://en.wikipedia.org/wiki/Esophagitis), dan ada polip di kerongkongan saya yang ditolak dokter untuk diangkat karena esophagitis tersebut. Kesehatan itu mahal, jadi memiliki banyak uang akan membuat saya lebih damai di dalam. Uang tidak bisa membelikanmu kebahagiaan, tapi pasti bisa meringankan beberapa masalah orang dewasa.

# Rencana masa depan
Saya harus fokus pada pemulihan dulu, sehingga saya bisa melanjutkan hidup saya. Setelah itu selesai, saya mungkin akan mengejar pembuatan konten sebagai hobi sambil mempertahankan pekerjaan saya sebagai insinyur perangkat lunak. Untuk situs web ini, saya mungkin akan memiliki tag terpisah untuk posting yang saya buat di sini, seperti pembaruan kehidupan, ulasan audio/keyboard, dll. Mungkin suatu hari saya mungkin mengejar pengembangan game untuk penghasilan pasif (*itu* juga hasrat saya) dan akhirnya membuat akun itch.io dan saluran youtube. Jika memang berakhir seperti itu, saya akan memperbarui tautan saya di situs web ini. Tujuan jangka panjang saya mungkin adalah ini:

- Mengejar S2, sehingga saya bisa menjadi dosen ketika saya pensiun dari programming sebagai pekerjaan utama.
- Belajar pengembangan game, desain 2D/3D, musik, dan pembuatan konten
- Belajar bahasa Jepang

---

Sekain dari saya. Saya harap ini adalah "situs web pribadi" terakhir yang saya buat, tetapi masa depan itu tidak pasti~