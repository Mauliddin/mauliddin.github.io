---
title: "Power Supply Untuk Wemos D1 Mini"
date: 2024-10-02
tags: ["article", "posts", "Wemos D1 mini", "Esp8266"]
---

Saya sedang mengerjakan sebuah proyek mesh network menggunakan Wemos D1 Mini (ESP8266). Awalnya, saya mencari solusi power supply yang hemat biaya untuk 10 perangkat Wemos D1 Mini. Saya sempat mempertimbangkan untuk menggunakan baterai lithium 18650, namun harganya cukup mahal.

Dilihat dari dokumentasi Wemos D1 Mini, tegangan kerjanya adalah 3,3 Volt. Saya berpikir untuk menggunakan 2 baterai 1,5 Volt menjadi 3 Volt, karena harga baterai 1,5 Volt cukup murah dibandingkan baterai lithium 18650. Namun, saya kurang yakin apakah itu akan cukup.

![pinout wemos d1 mini](https://miro.medium.com/v2/resize:fit:720/format:webp/1*Lw-73AM2e-8XReP5PIZGzw.png)

Setelah ditelusuri lagi, Wemos D1 Mini memiliki pin 5 Volt, sehingga saya memutuskan untuk menggunakan 3 baterai 1,5 Volt yang dirangkai seri menjadi 4,5 Volt. Setelah saya coba, ternyata bekerja untuk mengaktifkan Wemos D1 Mini.

