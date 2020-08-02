---
title: "Berkenalan dengan Composer"
excerpt: "Bagi kita yang baru memulai mengenal Laravel, kita harus berkenalan terlebih dahulu dengan satu tool (alat bantu) untuk menginstall Laravel, yang bernama Composer."
modified: 
categories: [Composer]
tags: [composer, perkenalan, pemula]
date: "2017-02-25T14:10:00+08:00"
draft: false
slug: "composer/berkenalan-dengan-composer"
---

Bicara tentang [Laravel](https://laravel.com), kita akan banyak menggunakan tehnik dan teknologi baru di dunia pemrograman PHP. Bagi kita yang baru memulai mengenal Laravel, kita harus berkenalan terlebih dahulu dengan satu *tool* (alat bantu) untuk menginstall Laravel, yang bernama [Composer](https://getcomposer.com).

Oke, sebagian kita mungkin sudah mengenal Composer sebelum kenal Laravel, tapi sebagian lagi mungkin baru tahu tentang Composer setelah belajar install Laravel (seperti saya). Nah, timbul beberapa pertanyaan seputar Composer :

1. Sebenarnya apa sih Composer itu?
2. Apa manfaatnya untuk kita jika menggunakan composer?
3. Kenapa laravel membutuhkan composer?

Ini adalah pertanyaan saya saat pertama tahu tentang Laravel dan Composer. Oke, kita akan membahas pertanyaan-pertanyaan tersebut di artikel ini.
## Apa itu Composer?
Menurut [websitenya](https://getcomposer.com), tagline Composer adalah “Dependency Manager for PHP”. Hmm... oke lah, kita simpan dulu tagline ini di memory.

Menurut bahasa saya, **Composer adalah** sebuah aplikasi yang diinstall ke dalam PC atau Laptop, yang memfasilitasi kita untuk dapat menggunakan *script/library* opensource milik orang lain ke dalam project yang sedang kita bangun. Lalu apa kaitannya pengertian itu dengan tagline “Dependency Manager”? Oke, kita bahas dulu tentang maksud dari “Dependency Manager”.

**Dependency Manager** di sini maksudnya, Composer akan mengelola “ketergantungan” antara *library-library PHP* (yang disebut *package*), yang **dibuat oleh seseorang** untuk **digunakan oleh orang lain**. Dan yang dikelola oleh Composer ini bukanlah *script* atau *library-*nya, tetapi ketergantungan (*dependency*) nya, antara satu *library* dengan *library* yang lain. Lalu ketergantugan atau *dependency* yang dimaksud itu bagaimana? oke, kita bahas tentang *dependency*.

### Analogi Dependency
Begini, misalkan kita membuat sebuah project *e-commerce* yang **memerlukan** fitur:
1. Fitur Keranjang Belanja
2. Fitur Penomoran Romawi untuk Invoice
3. Fitur Terbilang angka Rupiah untuk Invoice/Tanda Terima

Di atas kita bisa tangkap kata **"memerlukan"**. Artinya ketiga fitur itu **wajib ada** pada aplikasi e-commerce kita. Jika tidak ada? Maka bisa dipastikan aplikasi kita tidak akan berjalan sempurna (atau bahkan tidak bisa jalan).
Oke, karena ketiga fitur itu "wajib ada", maka kita harus membuatnya, *kan*?
Bagaimana kalau ada teman kita yang **sudah pernah membuat fitur Keranjang Belanja** untuk web e-commerce nya.
Kemudian ada **teman yang lain pernah membuat** fitur Konversi **Penomoran Romawi**.
Lalu **ada lagi** teman sudah **membuat** fitur **Terbilang** Rupiah.
Hhmm.. sepertinya temen-temen kita ini baik hati dan mau berbagi dengan kita. Dan ternyata ketiganya dengan senang hati memberikan *script* buatannya (diajarkan pula cara menggunakannya).

Apa yang terjadi? Akhirnya project *e-commerce* kita dapat selesai dikerjakan lebih cepat dari yang kita rencanakan. Tentu dengan cara ini, proses pembangunan aplikasi akan cenderung lebih cepat, karena untuk mendapatkan **fitur** tadi, kita **tidak perlu bikin dari awal**.

Jadi seperti itu contoh “ketergantugan” atau “*dependency*” ini. Sudah terbayang ya? Inti dari “dependency” adalah, project yang kita bangun “memerlukan” *script* atau *library-library* lain agar dapat berjalan dengan benar.

Betapa mudahnya hidup kita saat itu. Bisa kita bayangkan, jika banyak teman yang baik yang berbuat seperti itu, dapat berbagi script/library agar mempermudah pekerjaan orang lain. Hehe..

Dan ternyata ... hal itu sudah berlangsung saat ini. *Yap!* Saat ini ada banyak *developer/programmer* di berbagai belahan dunia saling berbagi *library* buatan mereka.

Pertanyaannya, bagaimana caranya agar kita bisa menggunakan *library-library* dari para programmer di belahan dunia lain? Sepertinya kita tidak bisa meminta mereka dengan mudah, *kenal aja nggak!?*

*Nah*, di sinilah peran kerja Composer ~~(masih ingat kan ya? kita ini lagi bahas composer)~~. Composer yang membantu kita dalam mendapatkan library-library PHP milik orang lain agar dapat digukanan dalam project kita.

Kira-kira sampai disini sudah terjawab ya pertanyaan nomor 2 di atas (**Apa manfaatnya untuk kita jika menggunakan composer?**)

### Terakhir, kenapa laravel membutuhkan composer?

Ya, karena Framework Laravel terdiri dari gabungan dari banyak *library PHP* yang diikat menjadi satu untuk menyempurnakan fitur-fitur yang ada pada Framework Laravel. Sepertinya sejak awal sudah didesain seperti itu. Keuntungkan untuk kita pengguna Laravel apa? Ya, ketika kita membutuhkan *library* lain, kita tinggal "memanggil" *library* tersebut melalui composer, dan *library* tersebut siap digunakan dalam project kita.

Sampai di sini akan muncul pertanyaan lagi, **bagaimana cara kerja composer** sehingga bisa se-"hebat" itu? Bisa mengumpulkan library milik orang lain dan membantu kita dalam penggunaannya dalam project kita?

Kita akan bahas pada artikel berikutnya, yaitu [Cara Kerja Composer dan Lumbung Library Packagist.org]({{< relref "2017-03-06-cara-kerja-composer" >}}).

Terima kasih untuk waktunya membaca artikel ini.
