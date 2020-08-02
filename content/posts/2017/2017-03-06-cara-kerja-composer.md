---
title: Cara Kerja Composer
excerpt: "Bagaimana cara kerja Composer yang berperan sebagai Dependency Manager untuk PHP?"
modified: 
categories: [Composer]
tags: [composer, cara-kerja, pemula]
date: "2017-03-06 14:10:00"
draft: false
slug: "composer/cara-kerja-composer"
---

Dengan [analogi kita sudah pahami mengenai *“Dependency”*]({{< relref "2017-02-25-berkenalan-dengan-composer" >}}), lalu apa yang dilakukan oleh Composer berkaitan dengan *tagline*-nya **“Dependency Manager for PHP”**?

Dari yang sudah kita ketahui sebelumnya, Composer adalah aplikasi yang berfungsi untuk men-*download* paket-paket atau *library-library* yang kita perlukan sebagai dependensi aplikasi kita. **Bagaimana cara kerja Composer** untuk membantu kita?
## Cara Kerja Composer
Sebelum men-*download* *library-library* yang kita perlukan, Composer akan:
1. Mengecek apakah *library-library* ini memerlukan *library* lain sebagai dependensinya?
2. Mengecek versi PHP dan *module-module* PHP yang diperlukan oleh *library-library* tersebut.

Setelah kedua proses di atas, Composer mendownload *library-library* tersebut ke dalam aplikasi/*project* kita pada direktori `“vendor”`.

Misalkan **versi PHP** yang terinstall di PC kita **tidak cocok dengan versi minimum** yang dibutuhkan oleh salah satu *library*, maka Composer akan memberitahukan bahwa "spesifikasi minimum tidak terpenuhi".
Atau ketika ada *module* PHP yang diperlukan oleh salah satu *library* belum terinstall atau *enabled*, Composer juga akan memberitahukan dan menyarankan kita untuk menginstall/*enable* *module* terlebih dahulu.

Jadi selain mengecek dependensi *library*, Composer juga membantu mengecek spesifikasi PHP kita apakah cocok atau tidak dengan kebutuhan *library* tersebut.
<h3>Contoh Kasus</h3>
Contoh kasus saat kita membuat sebuah aplikasi, kita memerlukan paket/*library* dari Composer :
- **Paket A**,
- **Paket B**, dan
- **Paket C**

Maka tahap yang dilakukan oleh Composer adalah :

1. Composer akan mengecek dependency dari paket A, B dan C tersebut beserta spesifikasi PHP-nya.
2. Kemudian Composer mendapatkan :
    - **Paket A**: memiliki dependecy **paket D**, **paket E**, dan **paket F**
    - **Paket B**: memiliki dependency **paket D** dan **paket G**
    - **Paket C**: memiliki dependecy **paket E** dan **paket H**
3. Composer** akan** men-*download* :
    - **Paket A**: ini paket yang kita butuhkan
    - **Paket B**: paket yang kita butuhkan
    - **Paket C**: paket yang kita butuhkan
    - **Paket D**: dibutuhkan oleh **paket A** dan **paket B**
    - **Paket E**: dibutuhkan oleh **paket A** dan **paket C**
    - **Paket F**: dibutuhkan oleh **paket A**
    - **Paket G**: dibutuhkan oleh **paket B**
    - **Paket H**: dibutuhkan oleh **paket C**
4. **Sebelum** mulai men-*download library* di atas, Composer akan mengecek lagi apakah ada dependensi untuk **paket D, E, F H,** dan **H**.
5. Jika Composer menemukan bahwa **Paket G** memiliki dependensi berupa **Paket I**, maka Composer juga akan mendownload paket I tersebut (karena diperlukan oleh paket G).
6. Jadi total ada **9 buah paket/*library*** yang akan di-*download* oleh Composer, sesuai dengan ketergantungan dari satu paket dengan paket lainnya.
    - **Paket A**: ini paket yang kita butuhkan
    - **Paket B**: paket yang kita butuhkan
    - **Paket C**: paket yang kita butuhkan
    - **Paket D**: dibutuhkan oleh **paket A** dan **paket B**
    - **Paket E**: dibutuhkan oleh **paket A** dan **paket C**
    - **Paket F**: dibutuhkan oleh **paket A**
    - **Paket G**: dibutuhkan oleh **paket B**
    - **Paket H**: dibutuhkan oleh **paket C**
    - **Paket I**: dibutuhkan oleh **paket G**

Nah kira-kira begitu **cara kerja Composer** menurut yang saya pahami :)

Mungkin pertanyaan berikutnya, dari mana ya Composer bisa tahu tentang dependensi *library-library* yang kita butuhkan itu? Nah, untuk menjawab pertanyaan tersebut, kita ulas tentang "lumbung" *library* dari Composer.

## Packagist.org

Misal kita ingin membuat sebuah paket atau* library* agar dapat digunakan oleh orang lain (melalui Composer), apa yang kita harus lakukan?

Jadi kita (atau seorang developer) yang membuat sebuah *library*, harus memberitahukan terlebih dulu tentang *library* yang dibuatnya tersebut kepada Composer. Memberitahukan ke mana? Yaitu ke ***repository* tempat yang menjadi rujukan Composer**, yaitu **<a href="https://packagist.org/" target="_blank">packagist.org</a>**.

Kalau teman-teman belum tau apa itu* repository*, analoginya repository itu semacam "lumbung", tempat di mana seluruh *library*, serta informasi terkait *library* yang ada pada Composer dapat kita temukan. Jadi Composer akan mencari paket-paket yang kita butuhkan itu dari "lumbung" yang bernama **packagist.org** tadi.

Lalu apa saja yang diberitahukan oleh seorang developer sebuah *library* kepada packagist.org agar dapat digunakan oleh orang lain?

### Syarat “publish” Paket

Syarat sebuah library yang didaftarkan pada packagist.org :
1. Nama dan deskripsi *library*
2. *Source code* dari paket atau *library* yang dibuat (biasanya dari github)
3. Versi (minimal) PHP dan atau *module* yang digunakan (opsional)
4. Daftar *library *lain yang menjadi dependensinya (opsional).

Teman-teman bisa melihat referensi ini di [https://packagist.org](https://packagist.org).

Nah kalau kita lihat **syarat yang ke empat**, di sini sang developer memberitahukan kepada *packagist*, bahwa “jika seseorang ingin menggunakan *library* saya ini, maka *library-library* yang saya list di syarat ke empat tadi juga harus di-*download*.” *Btw*, “pemberitahuan” yang dilakukan oleh sang developer *library* ke Packagist.org ini disebut dengan *“Publishing Package”* atau mempublish paket.

Nah, setelah *library* ter-*publish* atau diberitahukan ke packagist.org, Composer merujuk kepada list depedensi *library *yang telah di-*publish* tadi.

Jadi Composer membuat semacam “daftar isi” depedensi paket-paket/*library-library* yang ada di dalam repository packagist.org tadi.

## Simpulan Materi
Oke, sedikit kita simpulkan untuk tulisan tentang composer ini.

#### Apa manfaat Composer?
1. Berbagi *library* *open-source* kepada orang lain
2. Mempermudah kita mendapatkan paket/*library open-source* tanpa perlu mengetahui dependensi paket yang kita perlukan (karena dependensi di-*download* otomatis oleh Composer)
3. Mempermudah *update* paket *library* yang menjadi dependensi (tanpa dilakukan secara manual)

Nah jadi kira-kira begitu lah cara kerja **Composer sebagai "Dependency Manager for PHP"**, sebuah aplikasi yang membantu mempermudah kita dalam membuat sebuah aplikasi.

Sekarang pertanyaannya, apakah dengan membaca artikel tersebut teman-teman sudah memahami tentang
[Analogi Dependensi]({{< relref "2017-02-25-berkenalan-dengan-composer" >}}) dan
[Cara Kerja Composer]({{< relref "2017-03-06-cara-kerja-composer" >}})?

Jika belum paham, jangan sungkan untuk bertanya di komentar :)

Selanjutnya kita bahas tentang [Cara Install Composer](#).
