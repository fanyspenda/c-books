# Clean Code
A Handbook Of Agile Software Craftmanship

> **Note:**
> 
> Markdown ini berisi summary dari yg telah saya baca. Tidak semuanya saya tulis di sini. Jadi, tetap pertimbangkan untuk membaca langsung bukunya.

# Daftar Isi
- [Clean Code](#clean-code)
- [Daftar Isi](#daftar-isi)
- [Penamaan](#penamaan)
  - [Berikan nama yang sesuai/berarti](#berikan-nama-yang-sesuaiberarti)
  - [Hindari Disinformasi](#hindari-disinformasi)
  - [Berikan Pembeda yang Jelas](#berikan-pembeda-yang-jelas)
  - [Gunakan Nama yang Mudah Diucap](#gunakan-nama-yang-mudah-diucap)
  - [Gunakan Nama yang mudah Dicari](#gunakan-nama-yang-mudah-dicari)
  - [Hindari Encoding](#hindari-encoding)
  - [Member Prefix](#member-prefix)
  - [Interface dan Implementasinya](#interface-dan-implementasinya)
  - [Class Name dan Method Name](#class-name-dan-method-name)
  - [Gunakan 1 Kata per Konsep](#gunakan-1-kata-per-konsep)
  - [Jangan gunakan kata yang Ambigu](#jangan-gunakan-kata-yang-ambigu)
  - [Use Solution Domain Names](#use-solution-domain-names)
  - [Use Problem Domain Names](#use-problem-domain-names)
  - [Berikan Konteks yg Jelas](#berikan-konteks-yg-jelas)
  - [Hati-hati dalam Memberikan Konteks](#hati-hati-dalam-memberikan-konteks)
- [Functions](#functions)
  - [Kecil](#kecil)
  - [Block dan Indentasi](#block-dan-indentasi)
  - [Cuma melakukan 1 Kerjaan](#cuma-melakukan-1-kerjaan)
  - [Satu Level Abstraksi](#satu-level-abstraksi)
  - [Gunakan Top-Down Narative.](#gunakan-top-down-narative)
  - [`Switch` statement](#switch-statement)
  - [Nama yang Deskriptif](#nama-yang-deskriptif)
  - [Function arguments / Parameter](#function-arguments--parameter)
  - [Output Argument / Parameter](#output-argument--parameter)
  - [Flag argument](#flag-argument)
  - [Tidak punya side effect](#tidak-punya-side-effect)
  - [Error Handling adalah 1 kerjaan](#error-handling-adalah-1-kerjaan)
  - [DRY (Dont Repeat Yourself)](#dry-dont-repeat-yourself)
  - [Structured Programming](#structured-programming)
  - [Jadi, gimana sih nulis fungsi yg bener itu?](#jadi-gimana-sih-nulis-fungsi-yg-bener-itu)
- [Comments](#comments)
  - [Mindset soal *Comment*](#mindset-soal-comment)
  - [Comment Bukan Untuk kodingan yang Buruk (Bad Code)](#comment-bukan-untuk-kodingan-yang-buruk-bad-code)
  - [Komentar yang Diperbolehkan/baik](#komentar-yang-diperbolehkanbaik)
    - [Copyright / Terkait Legalisasi](#copyright--terkait-legalisasi)
    - [Komentar yang Informatif](#komentar-yang-informatif)
    - [Komentar yang Menjelaskan Tujuan](#komentar-yang-menjelaskan-tujuan)
    - [Komentar yang Mengklarifikasi Sesuatu](#komentar-yang-mengklarifikasi-sesuatu)
    - [Peringatan / Menjelaskan Konsekuensi](#peringatan--menjelaskan-konsekuensi)
    - [TODO comments](#todo-comments)
  - [Komentar yang Buruk](#komentar-yang-buruk)
    - [Tidak jelas](#tidak-jelas)
    - [Redundan](#redundan)
    - [*Comment* yang misleading](#comment-yang-misleading)
    - [Journal comment](#journal-comment)
    - [Komentar yang Tidak Perlu (Noise Comment)](#komentar-yang-tidak-perlu-noise-comment)
    - [Komentar di kurung tutup](#komentar-di-kurung-tutup)
    - [Komentar `Created by`](#komentar-created-by)
    - [Kode yang dikomentar](#kode-yang-dikomentar)
    - [Komentar bentuk HTML](#komentar-bentuk-html)
    - [Komentar yang non-local.](#komentar-yang-non-local)
    - [Informasi yang terlalu banyak](#informasi-yang-terlalu-banyak)
- [Formatting](#formatting)
  - [Tujuan dari Formatting](#tujuan-dari-formatting)
  - [Vertical Formatting](#vertical-formatting)
    - [File size](#file-size)
    - [Metafora Surat Kabar](#metafora-surat-kabar)
    - [Jarak 1 Line Tiap Konsep](#jarak-1-line-tiap-konsep)
    - [Vertical Density](#vertical-density)
    - [Jarak Vertikal](#jarak-vertikal)
  - [Horizontal Formatting](#horizontal-formatting)
    - [Panjang Line](#panjang-line)
    - [Horizontal Alignment](#horizontal-alignment)
    - [Indentasi](#indentasi)
  - [Aturan Tim](#aturan-tim)
- [Object Dan Data Structure](#object-dan-data-structure)
  - [Data Abstraction](#data-abstraction)
  - [Data/Object Anti-Symmetry](#dataobject-anti-symmetry)
  - [The Law of Demeter](#the-law-of-demeter)
  - [Data Transfer Object](#data-transfer-object)
    - [Active Record](#active-record)
- [Error Handling](#error-handling)
  - [Gunakan `Exception` daripada Return Error](#gunakan-exception-daripada-return-error)
  - [Selalu Mulai Dengan `Try-Catch-Finally`](#selalu-mulai-dengan-try-catch-finally)
  - [Berikan Context dalam `Exception`](#berikan-context-dalam-exception)
  - [Wrap Error](#wrap-error)
  - [Definisikan Normal Flow](#definisikan-normal-flow)
  - [Jangan Mereturn `Null`](#jangan-mereturn-null)
  - [Jangan Passing `Null`](#jangan-passing-null)
- [Boundaries (Batasan)](#boundaries-batasan)
  - [Third-Party App/Library](#third-party-applibrary)
  - [Mempelajari dan Explore App Pihak Ketiga](#mempelajari-dan-explore-app-pihak-ketiga)
- [Unit Tests](#unit-tests)
  - [TDD (Test-Driven Development)](#tdd-test-driven-development)
  - [Test yang membuat kodemu flexible](#test-yang-membuat-kodemu-flexible)
  - [Lebih sedikit `assert` yang perlu di test itu lebih baik](#lebih-sedikit-assert-yang-perlu-di-test-itu-lebih-baik)
  - [1 Konsep per Test](#1-konsep-per-test)
  - [FIRST](#first)
- [Classes](#classes)
  - [Kecil](#kecil-1)
  - [Single Responsibility Principle](#single-responsibility-principle)
  - [Kohesi](#kohesi)
  - [Mengorganisir Perubahan](#mengorganisir-perubahan)
    - [Isolasi terhadap perubahan](#isolasi-terhadap-perubahan)
- [System](#system)
  - [Taruh di *main*](#taruh-di-main)
  - [Factories](#factories)
  - [Dependency Injection](#dependency-injection)
- [Emergence](#emergence)
  - [Simple Design Rule 1: Menjalankan semua test](#simple-design-rule-1-menjalankan-semua-test)
  - [Simple Design Rule 2-4: Refactoring](#simple-design-rule-2-4-refactoring)
    - [Tidak boleh ada duplikasi](#tidak-boleh-ada-duplikasi)
    - [Expressive](#expressive)
    - [Minimalisir jumlah class dan method](#minimalisir-jumlah-class-dan-method)
- [Concurrency](#concurrency)
  - [Kenapa Concurrency?](#kenapa-concurrency)
  - [Mitos dan Miskonsepsi](#mitos-dan-miskonsepsi)
  - [Tantangan penggunaan concurrency](#tantangan-penggunaan-concurrency)
  - [Prinsip Yang Bisa Melindungi Kode Kalian](#prinsip-yang-bisa-melindungi-kode-kalian)
    - [SRP (Single Responsibility Principle)](#srp-single-responsibility-principle)
    - [Corollary: Batasi Scope Data](#corollary-batasi-scope-data)
    - [Corollary: Copy Data](#corollary-copy-data)
    - [Corollary: Thread Harus Seindependen Mungkin](#corollary-thread-harus-seindependen-mungkin)
  - [Kenali Librarymu](#kenali-librarymu)
  - [Kenali Model Ekesekusi Concurrencymu](#kenali-model-ekesekusi-concurrencymu)
    - [Producer-Consumer](#producer-consumer)
    - [Readers-Writers](#readers-writers)
    - [Dining Philosopher](#dining-philosopher)
  - [Jaga agar Sinkronisasi Tetap Kecil](#jaga-agar-sinkronisasi-tetap-kecil)
  - [Membuat kode shut-down itu tidak mudah](#membuat-kode-shut-down-itu-tidak-mudah)
  - [Testing Threaded Code](#testing-threaded-code)
# Penamaan
Kode yang baik adalah kode yang memiliki penamaan variable/fungsi yang baik juga.
## Berikan nama yang sesuai/berarti
Gunakan nama sesuai tujuannya. Contoh: daripada memberikan nama `int d`, lebih baik gunakan nama `int counter`.
## Hindari Disinformasi
Nama seperti `MapMarker` bisa menjadi masalah jika tipe variable tersebut bukanlah map, karena map mempunyai arti lain dalam dunia programming. Programmer lain bisa saja mengira MapMarker memiliki arti bahwa variable tersebut bertipe `Map[]`. 

Akan lebih baik jika variable tersebut bernama `GameMapMarker`, atau `marker` disini bisa menjadi *field* seperti `GameMap.Marker`.

Hindari juga penggunaan nama yang terlalu panjang dan hampir sama dengan nama variable lain. Contoh: `UserProfileConfigurationHandlerFunction` dengan `UserProfileConfigurationServiceFunction`.

## Berikan Pembeda yang Jelas
terkadang kita membuat variable dengan tipe yang sama dalam 1 function dan menamainya dengan:
```Go
string name1
string name2
```
Penamaan ini tidak disinformatif, tapi tidak juga informative (tidak memberikan informasi apa-apa). Lebih baik gunakan seperti berikut:
```Go
string firstName
string lastName
```

Contoh lain adalah `UserData` dan `UserInfo`. Kita tidak bisa tahu perbedaan kedua variable tersebut. Lebih baik berikan nama yang sesuai dengan maksud dari variable tersebut, seperti `user` dan `userDetail`.

## Gunakan Nama yang Mudah Diucap
Gunakan nama seperti:
```
Configuration
Product
Inventory
```
daripada:
```Go
Cfg
Prd
Inv
```

## Gunakan Nama yang mudah Dicari
Jika bikin function soal configuration, gunakan nama seperti:
```Go
configuration, config
```
jangan seperti ini:
```Go
xCxOxNxFxIxG
```

## Hindari Encoding
Penggunaan type data pada nama variable/function itu tidak baik, terlebih jika program yang kita tulis sudah ditulis jelas tipe datanya. 

Misal:
```Go
string usernameString
```
cukup jadi gini:
```Go
string username
```

> **Note**:
> Buat Case dibawah, sepertinya masih bisa dimaklumi, misal sudah ada variable bernama `bool isAvailable`, dan kita butuh *isAvailable* dalam bentuk string.
> ```Go
> bool isAvailable
> string isAvailableString
> ```

## Member Prefix
Cant understand this. :(
## Interface dan Implementasinya
mungkin ini hanya relate pada bahasa `Java` saja.

Biasanya kita mungkin akan menamai interface dengan nama, contoh `IConfiguration` dan `Configuration`. Akan lebih baik jika bernama tetap `Configuration` dan implementasinya dinamai `ConfigurationImplementation`.

## Class Name dan Method Name
Gunakan kata benda untuk Nama kelas.

Gunakan kata kerja untuk Nama Method.

## Gunakan 1 Kata per Konsep
Misal, untuk mengambil data dalam bentuk pagination, gunakan 1 kata saja, misal `Get`. Jangan ada frasa lain seperti `Fetch`, `Retrive`, dll.

Ketika ada logic lain, misal mengambil data tanpa pagination, kita bisa gunakan frasa lain (atau kata lain. Lihat [*Jangan gunakan kata yang Ambigu*](#jangan-gunakan-kata-yang-ambigu)).

## Jangan gunakan kata yang Ambigu
Jika ngikut aturan 1 Kata per Konsep di atas, kita akan banyak menemukan kata yang sama seperti `Add...`. Usahakan berikan nama function yang tidak ambigu. Misal, `Add...` untuk menambahkan value ke objek, `Insert...` untuk menambahkan data ke DB.

## Use Solution Domain Names
Cant understand this. :(
## Use Problem Domain Names
Cant understand this. :(
## Berikan Konteks yg Jelas
variable `name, address, city` dalam function `InsertUserAddress` mungkin sudah jelas. Tapi bagaimana jika variable `city` sendirian di function `sendPackage`?

Lebih baik gunakan nama seperti `destinationCity`.

## Hati-hati dalam Memberikan Konteks
Misal kita kerja di perusahaan `XYZ`. Jangan menamai variable kita dengan `XYZusername`, `XYZConfiguration`, dll. Selain tidak informatif, ini juga memberikan prefix yang tidak perlu.

# Functions
Function atau fungsi bertujuan untuk memudahkan programmer dalam membaca kodenya, bukan malah mempersulitnya.

## Kecil
Function harus kecil. Bagaimana menentukan apakah function itu kecil? Lanjut ke pembahasan berikutnya.

## Block dan Indentasi
Hindari nested-block/indentation. Penggunaan nested-block atau nested-indentation menandakan bahwa function kita masih belum cukup kecil.

## Cuma melakukan 1 Kerjaan
Jika kita membuat function, pastikan function tersebut hanya melakukan 1 tugas saja, tidak boleh lebih dari itu.

contoh function yang melakukan lebih dari 1 pekerjaan
```go
func insertItemsToCart(items []item) error {
    var totalPrice = 0
    for i, item := range items {
        totalPrice += item.Price
    }

    err := database.InsertToCart(items, totalPrice)
    return err    
}
```

akan lebih baik jika:
```go
func insertItemsToCart(items []item) error {
    totalPrice := calculateTotalPrice(items)
    err := database.InsertToCart(items, totalPrice)
    return err
}
```

## Satu Level Abstraksi
Jika function tersebut memiliki high-level abstraction (penggunaan fungsi yang mudah dimengerti), maka usahakan dalam function tersebut hanya berisi penggunaan function yang mudah dimengerti saja.

Jika suatu function berisi hal-hal yang low-level (seperti `array.append()`, dll), maka function tersebut sebaiknya tetap berisikan hal-hal dengan low-level abstraction saja.

## Gunakan Top-Down Narative.
Contoh dari case di atas:

> TO insert items to cart, we calculate the total price of items, then we insert items and total price to database.
> > To calculate total price, we do an interation of items and sum their prices.
> 
> > To Insert item and total price to database, we ...

## `Switch` statement
penggunaan switch statement hanya boleh 1 kali dalam 1 function.

## Nama yang Deskriptif
Berikan nama function yang deskriptif, menjelaskan apa maksud dari function itu. 

> *Nama yang panjang dan jelas itu lebih baik daripada nama yang pendek tapi tidak jelas.*

> *Nama yang panjang dan jelas itu lebih baik daripada comment yang panjang dan jelas.*

Setelah itu, tetap konsisten dalam menggunakan nama. Misal, untuk function yang mempersiapkan suatu data sebelum suatu proses dimulai, kita gunakan kata nama `prepare...`. Jika ada proses lain yang juga membutuhkan preparasi data, maka kita harus tetap menggunakan nama `prepare...` untuk proses tersebut. Contoh:


```go
func insertItems(items []item) {
    preparedItems := prepareInsert(items)
    db.InsertItems(preparedItems)
}

...

func updateItems(items []item) {
    preparedItems := prepareUpdate(items)
    db.UpdateItems(preparedItems)
}
```

## Function arguments / Parameter
Fungsi yang ideal itu fungsi yang tidak memiliki parameter (`niladic`).

Fungsi yang memiliki 1 parameter disebut `monadic`.

Fungsi yang memiliki 2 parameter disebut `dyadic`.

Fungsi yang memiliki 3 parameter disebut `triadic`.

Fungsi yang memiliki lebih dari 3 parameter disebut `polyadic`.

Semakin banyak parameter yang digunakan, semakin sulit dalam melakukan testing terhadap function tersebut. Semakin sulit pula memprediksi apa yang terjadi dalam fungsi itu. Hal itu juga bisa menjadi indikator bahwa fungsi kita mungkin tidak cukup kecil untuk dikatakan sudah *clean*.

> *Hindari penggunaan fungsi dengan parameter lebih dari 2 (3 ke atas).*
>
> *Jika membutuhkan lebih dari 2 parameter, ganti param menjadi object.*

## Output Argument / Parameter
Hindari pengunaan parameter fungsi sebagai output, karena ini bikin bingung.
Contoh:
```Go
func addItem(items *[]item) {}
```
Akan lebih baik jika ditulis:
```Go
func addItem(items []item) (newItems []item) {}
```

## Flag argument
Hindari penggunaan function dengan parameter sebagai *flagging*. Fungsi dengan flagging parameter, secara tidak langsung, mengakatan bahwa jika `true`, lakukan ini. Jika `false`, lakukan itu. Hal ini jelas melanggar aturan 1 fungsi hanya melakukan 1 kerjaan.

Contoh, kita akan membuat fungsi tentang merender halaman saat ini, atau halaman keseluruhan. Daripada kita membuat fungsi seperti ini:
```Go
func render(isAllPage true) {
    if isAllPage {
        // logic render semua halaman
    } else {
        // logic render halaman sekarang
    }
}
```
Akan lebih baik jika function di dalam `render()` dipisah menjadi:
```Go
func renderAllPage() {}
func renderCurrentPage() {}

func pageRenderer(criteria renderCriteria) {
    ....
    if criteria.RenderCurrentPage {
        renderCurrentPage()
    } else {
        renderAllPage()
    }
}
```

> ***Note:***
> 
> Jika argument didalam suatu fungsi diperlakukan sama, seperti pada contoh di bawah:
> ```go
> printMessage("%s-%s-%s", username, birthMonth, address)
> ```
> Maka fungsi `printMessage` masih dianggap fungsi dengan 2 parameter karena `username`, `birthMonth`, dan `address` masih dianggap satu kesatuan.
> 
> Apabila dituliskan, maka function tersebut dapat berbentuk demikian:
> ```go
> func printMessage(message, ...args) {...}
> ```

## Tidak punya side effect

fungsi yang baik tidak memberikan side effect. Contoh Side Effect:
```go 
func checkPassword(string password) {
    hashedPassword := db.GetUserHashedPassword(password)
    if hashedPassword == hash(password) {
        session.Start()
    }
}
```

Fungsi di atas memberikan side effect berupa, ketika user melakukan check password, fungsi di atas juga akan memulai sebuah *session*. Sehingga, ketika user melakukan check password kembali, akan terjadi error karena session yang sekarang sedang aktif.

akan lebih baik jika functinon itu diganti namanya menjadi:
```Go
func checkPasswordAndStartSession(string password) {
    ...
}
```

Dan akan lebih baik lagi jika `startSession` dan `checkPassword` dibuat menjadi 2 function yang berbeda.

## Error Handling adalah 1 kerjaan
Artinya, buat function sendiri untuk error handling jika memungkinkan. Jangan jadi satu seperti ini:
```go
func InsertNewItem(item Item) error {
    err := db.InsertNewItem(item)
    if err != nil {
        // logic handling error
    }
    
    return nil
}
```

tapi, lakukan seperti ini:
```go
func InsertNewItem(item Item) error {
    err := db.InsertNewItem(item)
    if err != nil {
        onError(err)
    }
    
    return nil
}
```

## DRY (Dont Repeat Yourself)
Cukup jelas di sini. Logic yang sama tidak perlu ditulis ulang. Buat function untuk memasukkan logic tersebut. Ini akan menghemat waktu dan memudahkan programmer lain dalam memahami kode kita.

## Structured Programming
*Edsger Dijkstra* dalam *structured programming* mengatakan bahwa setiap fungsi, dan setiap blok dalam fungsi, harus hanya ada 1 jalan masuk dan 1 jalan keluar. Artinya tidak boleh ada fungsi yang memiliki lebih dari 1 `return`, `break` atau `continue` dalam perulangan, ataupun `goto` (dalam C).

Dalam fungsi yang kecil, terkadang penggunaan `return`, `break`, atau `continue` dapat membantu kita lebih ekspresif dalam menuliskan kode.

Jika kode kita besar, tentu penggunaan `return`, `break`, atau `continue` dapat membuat fungsi kita memiliki terlalu banyak jalan keluar, dan itu tidak baik. 

## Jadi, gimana sih nulis fungsi yg bener itu?
Buat Fungsi seolah-olah kita sedang membuat suatu narasi cerita. Sebuah perjalanan data yang mudah dipahami oleh pembaca kode kita.

Memahami clean code bukan berarti langsung jago menerapkan semua teori yang dijelaskan di atas tadi. Kadang Penulis (*Robert C. Martin*), juga membuat fungsi dengan panjang dan kotor. Tapi, setelah itu, ia merapikan fungsi tersebut.

# Comments

## Mindset soal *Comment*
Komentar adalah tanda ***kegagalan*** kita sebagai programmer untuk membuat suatu kode yang ekspresif. Sehingga, kita menambahkan komentar untuk kode kita. harusnya kita malu jika kita menambahkan komentar di kode kita karena kita telah gagal menjelaskan kode kita pada pembaca kode kita.

Komentar juga adalah pembohong. Ia bisa *membusuk* seiring berkembangnya kode kita. Dan akhirnya, komentar tersebut tidak relevan lagi.

Misal, kita membuat komentar untuk fungsi ini:
```Go
// add one item to database
func Add(item Item) {}
```

lalu, kode kita berkembang menjadi seperti ini:
```Go
// add one item to database
func Add(items []Item) {}
```
Jika dilihat, komentar tidak diupdate setelah ada perubahan fungsi. Programmer mungkin saja lupa mengupdate komentar dari fungsi tersebut, sehingga komentar itu sudah tidak relevan dan bahkan menjadi sebuah misinformasi kepada programmer lain.

Tapi, tentu komentar hanyalah alat. Baik atau buruknya, tergantung penggunanya.

## Comment Bukan Untuk kodingan yang Buruk (Bad Code)
Komentar bukanlah untuk kodingan kita yang buruk/sulit dipahami. Jika kita merasa kodingan kita sulit dipahami, jangan tulis komentar, tapi benerin kode kita.

## Komentar yang Diperbolehkan/baik
### Copyright / Terkait Legalisasi
contoh:
```Go
// Copyright (C) 2020 by ....
// Relase Under Term of ...
```

### Komentar yang Informatif
Komentar yang informatif memanglah baik, tapi kode yang informatif tetaplah lebih baik.

### Komentar yang Menjelaskan Tujuan

### Komentar yang Mengklarifikasi Sesuatu
Contoh:
```Go
// use max limit = 100
// because 1 data is big enough.
// fetching more than 100 data at once will slow down the service.
if limit > 100 {
    limit = 100
}
```

### Peringatan / Menjelaskan Konsekuensi
Contoh:
```Go
// Dont delete this function
func insertItems(items []item) {}
```

### TODO comments
Kadang kita ingin melakukan sesuatu terhadap kode kita, tapi waktu tidak memungkinkan. Sehingga, kita menambahkan komentar TODO ke kode kita sebagai pengingat bahwa ada yang perlu kita kerjakan di bagian tertentu dalam kode kita.
```Go
// TODO: add logger for this package
```

## Komentar yang Buruk

### Tidak jelas
Jika memang kita harus menambahkan komentar, luangkan waktu sehingga kita membuat komentar yang sebaik mungkin.

### Redundan
Jangan membuat kode yang tidak lebih mudah dipahami dibandingkan kodenya. Karena, kalau begitu, mending baca kodenya langsung daripada baca komentar. Komentar jadi terkesan membingungkan dan akhirnya jadi hal yang nambah-nambahin baris.

### *Comment* yang misleading

### Journal comment
Beberapa orang ada yang menambahkan komentar tentang hari dan aktifitas apa yang mereka lakukan di kode tersebut setiap kali mereka melakukan perubahan.

Dulu memang ini banyak diterapkan, tapi sekarang tidak.

### Komentar yang Tidak Perlu (Noise Comment)
Contoh:
```Go
// Day of the month
var dayOfMonth
```

### Komentar di kurung tutup
Beberapa orang memberikan komentar pada kurung tutup untuk menandai bahwa itu adalah akhir dari, entah `function`, `try-catch`, atau `switch-case`.
Ini tentu tidak baik.

Daripada membuat komentar seperti itu, lebih baik refactor fungsi kita supaya lebih kecil dan lebih mudah dipahami, sehingga tidak ada block yang terlalu panjang dan dalam.

### Komentar `Created by`
Tidak perlu menambahkan komentar seperti `// Added by John`. Kita sudah punya *versioning* sendiri seperti git untuk mengetahui kode tertentu ditambahkan/diubah oleh siapa. 

### Kode yang dikomentar
Kode yang dikomentari saat ini bisa menjadi masalah. Orang lain tidak akan berani menghapus kode tersebut karena mengira itu masih akan digunakan.

Lebih baik, jika kode sudah tidak digunakan, hapus. Jika dibutuhkan kembali, lihat di git/tool untuk versioning lainnya.

### Komentar bentuk HTML
Komentar dalam bentuk HTML itu sulit dibaca.
### Komentar yang non-local.
Komentar yang mengandung informasi global, tapi digunakan hanya pada 1 baris code saja.
Contoh:
```Go
// file1.go
...
// The default port is 8200
func initDB() {}

------------
// file2.go
func initDB() {}
```

Dan, tentu kode seperti ini tidak baik. Tidak ada yang bisa menjamin apakah selamanya port yang dipakai itu 8200 atau tidak (dan apakah akan ada yang mengupdate `comment`-nya).

### Informasi yang terlalu banyak
Cukup tuliskan informasi yang perlu diketahui oleh pembaca kode kita.
Komentar yang terlalu panjang pada fungsi kita juga bisa jadi tanda bahwa fungsi kita telah melakukan lebih dari 1 hal, dan itu perlu dibenahi.

# Formatting
Formatting di sini maksudnya adalah membuat kesan kode kita dapat dibaca dan dipahami oleh orang.

## Tujuan dari Formatting
Tujuan dari formatting adalah memudahkan komunikasi antar programmer, karena baik dalam komunikasi adalah ciri seorang programmer profesional.

Kode yang baik akan menjadi teladan untuk programmer lain, untuk mematuhi style dan penulisan kode. 

mungkin kode kita tidak akan bertahan dan akan berubah, tapi disiplin dan style kita dalam menulis kode yang baik akan tetap bertahan.

## Vertical Formatting
### File size
File size di sini maksudnya adalah berapa panjang kode yang perlu kita tulis dalam 1 file.

Tidak ada batasan khusus di sini. Tapi, penulis mengambil contoh beberapa library java. Dari situ, ditemukan bahwa dengan rata-rata 200 baris kode dalam 1 file, dengan batas maksimal 500 baris dalam 1 file, kita sudah bisa membuat sebuah sistem yang baik.

### Metafora Surat Kabar
Jika kita membaca surat kabar, berita-berita yang dituliskan biasanya runtut. Dari judul yang menjelaskan garis besar kejadian, rangkuman kejadian di paragraf-paragraf awal, hingga detail-detail dari kejadian tersebut di akhir.

Hal ini juga bisa diterapkan dalam kodingan kita. Berikan nama fungsi yang merangkum seluruh proses. Pastikan level atas memberikan gambaran umum tentang fungsi kita. Lalu, semakin ke bawah, kita berikan detail dari fungsi kita.

Contoh:
```Go
// ini fungsi high-level
// memberikan gambaran umum
func getUser(userId int) (user User) {
    user := getUserFromRedis(userId)
    if user != nil {
        return user
    }

    user := getUserFromDB(userId)
    return user
}

// ini fungsi yang lebih mendetail dari fungsi di atas.
func getUserFromRedis(userId int) {}
func getUserFromDB(userId int) {}
```

### Jarak 1 Line Tiap Konsep
Jika terdapat beberapa konsep dalam 1 fungsi, kita bisa memberinya jarak sebagai penanda bahwa suatu konsep sudah selesai dan konsep baru akan dimulai.

Contohnya pada fungsi `getUser()` di atas, ada jarak 1 baris antara `getUserFromRedis` dan `getUserFromDB`.

Hal ini akan memudahkan kita memberi batasan berpikir. Ketika sudah masuk pada bagian `getUserFromDB`, kita tidak perlu lagi memikirkan soal mengambil data dari redis lagi.

### Vertical Density
Pastikan kode tertulis rapat. Jangan ada komentar yang justru membuat jarak antar baris kode semakin jauh dan menjadi sulit dipahami (karena harus scroll atas-bawah terus).

### Jarak Vertikal
1. **Variable Declaration**
   
   Penulisan Variable harus dekat dengan penggunaannya.
   Jika fungsi kita cukup kecil, harusnya ini bukan masalah.

2. **Instansiasi Objek**
   Tidak ada aturan khusus, tapi biasanya ditulis di awal fungsi (atau awal class pada Java)

3. **Fungsi Dependensi**
   Fungsi dependensi ditulis dibawah fungsi yang memanggilnya dan dituliskan berurutan sesuai bagaimana fungsi pemanggilnya melakukan pemanggilan fungsi dependensi. Contoh:

   ```Go
   func mainFunction() {
       // dipanggil dari 1 ke 2
       func1()
       func2()
   }

   // ditulis urut sesuai pemanggilannya di mainFunction()
   func func1() {}
   func func2() {}
   ```

   Jangan seperti dibawah:
   ```Go
   func func2() {}

   func mainFunction() {
       func1()
       func2()
   }

   func func1() {}
   ```

4. **Kesamaan Konsep**
   Fungsi yang memiliki kesamaan konsep, dinamai dengan nama yang mirip dan diletakkan saling berdekatan. Contoh:
   ```Go
   // sama-sama menghitung bagian dari barang (harga dan diskon)
   func CalculateTotalPrice(items []Item) {}
   func CalculateTotalDiscount(discountedItems []items) {}
   ```

## Horizontal Formatting
### Panjang Line
Panjang line max 120 karakter

### Horizontal Alignment
Penulis buku ini berpendapat bahwa indentasi pada variable itu tidak perlu. Contoh:
```Go
var firstName string = "John"
var lastName  string = "Doe"
var age       int    = 27
```

Yang terpenting adalah jumlah variable yang dideklarasikan tidak terlalu banyak, sehingga baris tidak memanjang ke bawah.


### Indentasi
Indentasi sesuai dengan tanda kurung. Misal:
```Go
func PrintMessage() {
    print()
}
```
jangen seperti di bawah ini:
```Go
func PrintMessage() { print() }
```

## Aturan Tim
Setiap orang mempunyai style koding sendiri. Contoh, Ada yang menggunakan `a = a + 1`, ada yang `a += 1`, dll.

Jika kerja dalam sebuah tim, buat aturan tim untuk masalah formatting dan style dari kode. Agar tidak ada style kode yang berbeda-beda, sehingga membuat kode kita tidak konsisten.

# Object Dan Data Structure
> Objects menyembunyikan data dan mengekspos function yang mengoperasikan data tersebut.

> Data structure mengekspos data mereka dan tidak memiliki function.

Dari kata di atas, kita bisa simpulkan bahwa ***Objek*** itu:
1. Tidak boleh mempunyai variable public
2. Pengaksesan/pemrosesan variable dalam objek dilakukan melalui method yang dia punya

Sedangkan ***Data Structure*** berarti:
1. Memiliki variable yang bersifat publik
2. Tidak memiliki method.
## Data Abstraction
Abstraksi artinya kita tidak perlu membuat seseorang mengetahui detail dari sebuah kode secara langsung.

Tujuan dari abstraksi membuat kode kita menjadi mudah dimengerti dan menyembunyikan kerumitan kode kita. Contoh:

Berikut adalah contoh yang baik dalam membuat interface Persegi Panjang:
```Go
type Rectangle interface {
    getArea()
    getCircumference()
}
```
Contoh yang kurang baik seperti ini:
```Go
type Rectangle interface {
    // Kedua function ini bisa dijadikan objek yang bisa diakses saja,
    // daripada menggunakan method untuk mengaksesnya.

    // Lalu, tidak adanya `getArea()` dan `getCircumference()` menandakan
    // bahwa kita harus menghitung luas dan keliling sendiri.
    // Ini berarti tidak menyembunyikan keabstrakan kode kita.
    getLength()
    getWidth()
}
```
## Data/Object Anti-Symmetry
Cant Understand this :(

## The Law of Demeter
Cant Understand this :(

## Data Transfer Object
Bisa dibilang nama lain dari Data Structure (class dengan dengan variable public, tanpa fungsi).

DTO bisa ditulis dengan benar-benar memberikan akses public pada variabel, atau membuat variable private, tapi memiliki *setter* dan *getter*. Selain itu, tidak ada method lagi.

### Active Record
Active Record di sini berarti data structure yang memiliki method *Save()* dan *Find()* (bukan berarti method yang mengurusi bagian bisnis juga ditaruh di sini ya..).

# Error Handling

Error handling yang baik adalah error handling yang tidak membuat logic dalam kode menjadi samar.

## Gunakan `Exception` daripada Return Error
Sudah cukup jelas. Penggunaan Exception akan lebih membuat kode rapi daripada mereturn satu-per-satu error.

## Selalu Mulai Dengan `Try-Catch-Finally`
Dengan memulai menulis Try-Catch dan Finally, kita bisa dengan mudah menuliskan program dan error handling dengan runtut.

## Berikan Context dalam `Exception`
Context di sini bertujuan agar kita mendapat informasi dari error tersebut. Seperti dari mana error berasal, apa penyebabnya, dll.

## Wrap Error
Gabungkan error daripada menghandle satu-per-satu. Contoh:
```Go
func InsertItem(a item) {
    err := insertToDB(a)
    if err != nil {
        switch (err) {
            case errExec:
            // do something
            case errConnection:
            // do something
        }
    }

    return
}
```

lebih baik jika:
```Go
func InsertItem(a item) {
    err := insertToDB(a)
    handleError(err)
    return
}
```

## Definisikan Normal Flow
Kadang ada beberapa case khusus yang menghasilkan error, namun tidak perlu dihandle.

Jadi, buat case khusus dalam function/class terpisah.

## Jangan Mereturn `Null`
Hindari return function dengan value yang nullable. Hal ini membuat kita harus melakukan pengecekan apakah hasil function tersebut mereturn null atau tidak.

Pertimbangkan untuk menggunakan empty object/zero-value.

## Jangan Passing `Null`
Passing null ke function sebagai parameter lebih buruk dari mereturn null.
Hindari penggunaan ini.

# Boundaries (Batasan)

## Third-Party App/Library
Penggunaan library pihak ketiga sudah cukup lumrah dalam pengembangan software. Tapi, kadang library tersebut mengandung function yang memiliki banyak fitur secara umum, namun tak sesuai dengan segi bisnis aplikasi kita.

Oleh karena itu, buat function/class tersendiri yang membungkus proses aplikasi pihak ketiga tersebut agar sesuai dengan segi bisnis kita.

## Mempelajari dan Explore App Pihak Ketiga
Dalam menggunakan aplikasi/libary pihak ketiga, tentu kita perlu mempelajari library tersebut. Mempelajari hal itu tidak mudah, mengimplementasikannya juga tidak mudah. Mempelajari dan mengimplementasikannya adalah hal yang *double* tidak mudahnya.

Nah, daripada kita mempelajari app pihak ketiga tersebut di code production kita, lebih baik kita membuat code untuk mencoba library tersebut terlebih dahulu dan membuat testnya. Hal ini disebut dengan *learning test*.

learning test memiliki beberapa manfaat diantaranya:
1. Kita bisa memahami library yang dipakai tanpa merusak code yang sudah di production.
2. Jika ada update terkait library tersebut, kita bisa menjalankan testnya untuk memastikan apakah library tersebut memiliki perubahan *behaviour*. Contoh: Fungsi yang biasanya mereturn integer, di versi terbarunya mereturn string.

> **Note:**
>
> Usahakan aplikasi kita tidak terlalu banyak bergantung pada library/aplikasi pihak ketiga. Karena, aplikasi pihak ketiga adalah hal yang diluar kendali kita. Lebih buruknya, bisa jadi kita yang dikendalikan oleh aplikasi pihak ketiga.
>
> Kita bisa saja melakukan maintenance di code kita sendiri kapanpun, tapi tidak dengan aplikasi pihak ketiga.


# Unit Tests
## TDD (Test-Driven Development)
Banyak orang mengira bahwa TDD adalah menulis unit test terlebih dahulu sebelum menulis code kita. Namun, sebenarnya hal itu hanya bagian kecil dari TDD.

Berikut 3 hukum TDD:

1. Jangan menulis kode sampai kita membuat unit test yang gagal.
2. Jangan menulis unit test lebih dari cukup untuk case yang gagal, dan tidak bisa dicompile itu termasuk gagal. (Kalo unit test yang ditulis udh bisa gagal, yaudah, stop)
3. Jangan menulis kode lebih dari cukup untuk lolos dari unit test. (kalo code yang kita tulis sudah lolos unit test, bikin test case baru)

Membuat unit test itu sama pentingnya dengan menulis kodenya. Harus bersih sebersih code projectnya.

Unit test yang tidak bersih akan menjadi kendala ketika ada perubahan. Unit test akan semakin sulit dibaca dan membuat pengembangan aplikasi terhambat. Karena terhambat, tim manajerial akhirnya memutuskan untuk menghapus seluruh unit test. Akhirnya, bug bermunculan ketika terjadi perubahan.

Semakin banyak bugs, akhirnya developer semakin takut untuk mengubah kode yang sudah di production.

Unit test yang buruk itu setara, atau bahkan lebih buruk daripada tidak ada unit test sama sekali. Perlakukan unit test seperti kita memperlakukan kode project kita.

## Test yang membuat kodemu flexible
Dengan adanya unit test, kode kita menjadi flexible karena kita bisa membuat perubahan apapun selama unit test kita tetap berjalan.

Kita bisa mengimprove design dan arsitektur project kita tanpa takut merusak flow bisnis saat ini, karena hal itu telah dijaga oleh unit test yang baik.

## Lebih sedikit `assert` yang perlu di test itu lebih baik
Dengan lebih sedikitnya assert yang kita buat, artinya fungsi unit test kita bisa lebih fokus pada 1 assert. Tapi, bukan berarti banyak `assert` itu buruk. 

## 1 Konsep per Test
Buat setiap test menjadi hanya 1 konsep per test.

## FIRST
Testing harus memenuhi kriteria *FIRST* ini, yaitu:

1. **Fast:** Testing haruslah cepat. Jika tidak, kita akan malas menjalankan test secara berkala. Jika kita malas, maka testing akan menjadi tidak relevan. Ketika ada error, kita jadi kesulitan untuk membenahinya.

2. **Independent:** Testing haruslah independen (1 test tidak menjadi dependensi ke test lainnya).

3. **Repeatable:** Testing haruslah bisa dijalankan dalam berbagai environment. Baik dalam keadaan ada internet, maupun tidak. Baik di dev, ataupun di production.

4. **Self-Validating:** Testing harus bisa mengoreksi diri mereka sendiri (apakah testing ini berhasil/gagal). Kita tidak boleh menganalisa sendiri hasil dari testing. Biarkan program yang melakukannya untuk kita.

5. **Timely:** Testing harus ditulis sebelum kita menulis kode. Jika tidak. Jika tidak, tanpa kita sadari kita bisa jadi membuat kode yang tidak testable, sehingga kode kita menjadi sulit ditest.

# Classes
Di sini kita akan membahas bagaimana kelas (atau mungkin struct jika di golang) seharusnya ditulis.

## Kecil
Class haruslah kecil. Kelas tidak boleh memiliki jumlah properti yang besar. setiap properti merupakan *responsibility* (tanggungjawab) dari kelas itu.

Bayangkan sebuah kelas/struct dengan 70 field.
```Go
type superDashboard struct {
    menuName string
    activeMenu string
    userMenu string
    userMenuName string
    userMenuList string
    userMenuDetail string
    ...
    adminMenu string
    adminMenuName string
    adminMenuList string
    ...
}
```

Bagaimana kalau kita coba jadikan struct di atas seperti ini:
```Go
type superDashboard struct {
    GetUserMenu func() UserMenu
    GetAdminMenu func() AdminMenu
    ...
}
```

Apakah ini sudah kecil? **Bisa jadi *belum***.

Kelas diatas memang sudah berbentuk kecil, tapi dia masih memiliki banyak *responsibilities* seperti mengambil menu user, mengambil menu admin, dll.

Cobalah mendeskripsikan kelas yang akan kita buat tanpa menggunakan kata *Dan*, *Jika*, *Atau*, *Tapi*.

Coba kita deskripsikan superdashboard:
> SuperDasboard adalah kelas yang digunakan untuk mengambil data dari untuk keperluan menu user ***dan*** keperluan menu admin.

nah, kita bisa tahu bahwa ada kata *"dan"* di atas. Dengan begitu, kita bisa menyimpulkan bahwa superDashboard memiliki responsibility lebih dari satu, yang mana ini melanggar konsep ***Single Responsibility Principle*** (akan dibahas di bawah).

## Single Responsibility Principle
Suatu class hanya boleh punya 1 alasan untuk berubah.

Jika kelas kita memiliki lebih dari 1 responsibility, tentu hal ini akan membuat kelas kita memiliki lebih dari 1 hal untuk berubah. 

Misal, kelas superDashboard tadi. Akan ada 2 alasan untuk berubah:
1. Kelas akan berubah terkait dengan menu user
2. Kelas akan berubah terkait dengan menu admin

beberapa programmer mungkin berpendapat bahwa jika task sudah selesai, harus segera dideliver dan mengerjakan task selanjutnya. Kemudian, menganggap bahwa class yang kecil-kecil akan membuat bingung.

Tapi, analoginya gini:

kita pengen menyimpan semua perkakas kita ke dalam kotak peralatan dengan wadah-wadah kecil dan label yang jelas.

Atau kita mau menyimpannya dalam kotak peralatan dengan sedikit wadah besar tanpa label.

## Kohesi
Kohesi maksudnya adalah method yang dimiliki oleh kelas sebisa mungkin menggunakan seluruh variable yang dideklarasikan dalam kelas (tidak harus semua variable, tapi jika bisa saja).

Dengan begitu, kelas dan methodnya akan memiliki keterikatan yang kuat.

Jika ada fungsi yang tidak terikat dengan kelas, lebih baik dipisahkan/buat fungsi sendiri.

## Mengorganisir Perubahan
Perubahan pasti terjadi. Kadang kita perlu merombak sebuah kelas untuk menerapkan perubahan.

Namun, jika kelas kita secara logic sudah sesuai, kita tidak perlu menerapkan perubahan terlebih dahulu. Perubahan baru dirasa perlu jika ada perubahan dari segi bisnis atau logic.

Usahakan menrapkan konsep Open-Closed Principle, dimana konsep itu artinya setiap kelas menerima improvisasi/pengembangan, tapi tidak menerima modifikasi.

### Isolasi terhadap perubahan
Hindari penggunaan kelas yang memiliki dependensi pada implementasi.
Usahakan setiap kelas saling terhubung melalui *interface*. Ini akan memudahkan testing dan sekaligus menerapkan sebuah konsep design kelas yang bernama *Dependency Invesion Principle.*

*Dependency Inversion Principle* adalah konsep dimana kelas kita hanya boleh saling ber-dependency melalui interface atau bukan pada implementasi konkrit suatu method.

# System
Membangun sebuah sistem seperti merancang sebuah kota. Bagaimana kota bisa terbentuk dan tetap ada? Hal itu karena kota memiliki perancangan/konstruksi. Kemudian, setelah kota berhasil dibangun, unit-unit kecillah yang menjaga segala fungsi dalam kota tetap berjalan. Hal itu terjadi juga pada pembangunan sebuah hotel bertingkat. Ketika dalam masa pembangunan, terdapat alat berat, mesin-mesin yang menata segala pondasi dan tembok bangunan. Tapi, setelah bangunan selesai dibuat, tidak ada lagi mesin-mesin besar. Yang ada adalah pelayan kamar, resepsionis, penjaga keamanan, dll.

Begitu pula dengan membangun aplikasi. Sebuah aplikasi tentu memiliki bagian yang membangun semua fungsi terlebih dahulu, hal ini akan kita sebut *konstruktor*.

Tentu bukanlah hal yang baik membiarkan fungsi yang membangun sebuah aplikasi bercampur dengan fungsi bisnis aplikasi kita. Ibarat, tentu kita tidak ingin melihat ada buldozer di dalam kamar hotel kita.

## Taruh di *main*
Letakkan semua konstruktor di fungsi main. Semua yang membangun aplikasi kita agar tetap berjala, letakkan di dalam main function.

## Factories
Function main lebih baik tidak langsung terhubung dengan sebuah implementasi. Kita bisa menerapkan konsep Abstract Factory, dimana terdapat abstract untuk fungsi bisnis dan ada factory untuk membuat objek yang berisikan fungsi abstract tersebut. Dengan begitu, kita bisa memisahkan proses konstruktor dalam *main* dan mengontrol logic bisnis.

## Dependency Injection
Hal ini sebenarnya sudah diterapkan dalam clean architechture, dimana kita membuat sebuah package yang terpisah, misal antara logic bisnis dan management data.

Dengan terpisahnya beberapa hal tersebut akan membuat kode kita menjadi lebih testable

# Emergence
Menurut Kent Beck, ada design yang bernama Simple Design yang memiliki 4 aturan berikut:
1. Menjalankan semua test
2. Tidak ada duplikasi
3. Menjelaskan maksud dari programmer
4. Meminimalisir jumlah class dan method

Secara berurutan, peraturan di atas ditulis dari yang terpenting hingga yang paling ttidak penting.

## Simple Design Rule 1: Menjalankan semua test
Artinya, kode kita harus *testable* dan semua test yang kita buat harus berjalan dengan baik.

Tidak ada test atau gagal menjalankan test, artinya sistem belum terverifikasi, dan sistem yang belum terverifikasi sebaiknya tidak dideploy ke production.

## Simple Design Rule 2-4: Refactoring
Unit testing harusnya menghilangkan rasa takut ketika kita melakukan refactoring.

### Tidak boleh ada duplikasi
Duplikasi dapat menimbulkan masalah dan menambah pekerjaan. Misal: ketika ada bug dalam kode duplikasi kita, kita harus membenahi semua kode duplikasi kita karena mereka harusnya juga ngebug.

### Expressive
Usahakan kode kita mudah dipahami oleh orang lain, karena project kita itu long-term maintenance.

Jadi expressive bisa dengan cara memberi penamaan yang baik, membuat function lebih kecil, atau menggunakan standard tata nama.

Unit test yang jelas juga bisa termasuk ekspresif.

### Minimalisir jumlah class dan method
Biasanya, karena kita ingin selalu membuat function kita lebih kecil, akhirnya muncul banyak kelas dan method. Aturan ini untuk membatasi kita dalam membuat class dan method juga (intinya, jangan berlebihan!).

Ingat, aturan ini adalah aturan yang paling rendah. Jadi, yang terpenting adalah *semua test jalan, tidak ada duplikasi dan expresif*.

# Concurrency
Concurrency memisahkan antara apa yang harus diselesaikan dan kapan harus diselesaikan.

## Kenapa Concurrency?
Kita bisa menerapkan multithread /concurrency jika:
- Data yang dikelola banyak dan user butuh response cepat.
- Sistem bisa memberi response setelah pemrosesan yang berat selesai dilakukan.

## Mitos dan Miskonsepsi
- Concurrency meningkatkan performa
  
  Concurrency hanya meningkatkan performa jika ada waktu yang bisa dishare ke process lain secara bersamaan. 
  
  Misal, ngerebus mie ***sambil*** nyiapin bumbu itu lebih cepet dibanding ngerebus mie, ***baru*** nyiapin bumbu (Karena ngerebus mie itu lama, bisa sampe 3 menit).
- Design nggk berubah ketika menggunakan concurrency
  
  Design ikut berubah karena secara algoritma juga berubah. Design kode procedural (berurutan) itu berbeda dengan design kode concurrency.


Hal yang perlu diingat tentang Concurrency:
1. Concurrency menimbulkan beberapa hal. Baik secara performance dan kode yang kita tulis.
2. Concurrency itu complex, bahkan untuk masalah yg simple.
3. Cuncurrency bug itu kadang muncul, kadang nggk. 
4. Concurrency kadang memunculkan perubahan ke design sistem.

## Tantangan penggunaan concurrency
Tantangannya adalah concurrencynya balapan. Misal kita ada 2 thread menjalankan function `tambahAngka()` berikut:
```Go
var angka = 20
func tambahAngka() {
    angka++
}
```

Ada 3 kemungkinan yang bisa terjadi:
- thread 1 = 21 --> thread 2 = 22 --> Angka = 22
- thread 2 = 21 --> thread 1 = 22 --> Angka = 22
- thread 1 = 21 --> thread 2 = 21 --> Angka = 21

hasil yang ketiga adalah hasil yang tidak kita inginkan. Hal ini terjadi karena ada banyak jalan yang bisa dilalui concurrency. Tantangannya adalah, *bagaimana membuat concurrency melalui jalan yang kita inginkan*.

## Prinsip Yang Bisa Melindungi Kode Kalian
### SRP (Single Responsibility Principle)
Dengan SRP, kita bisa memastikan setiap function memiliki 1 tujuan. Pertimbangan dengan concurrency adalah:
1. Concurrency punya life-cyclenya sendiri. Ia berubah dan dimaintenance dengan cara berbeda dari non-concurrency code.
2. Concurrency memiliki challenges tersendiri. Artinya, concurrency mempunyai solusi tersendiri dan tidak bisa disamakan dengan non-concurrency code.
3. Masalah yang ditimbulkan dari penulisan concurrency yang tidak baik saja sudah membuat pusing. Jangan ditambah dengan kode lain yang tidak berhubungan dengan concurrencynya.

Jadi, pisahkan kode concurrency dengan kode lain.

### Corollary: Batasi Scope Data
Tidak jarang concurrency menggunakan shared object. Usahakan batasi jumlah section yang mengakses object tersebut. Semakin banyak section yang mengakses object tersebut, maka:
1. Kita bisa lupa untuk memprotect object tersebut, menyebabkan error, atau mungkin bug yang tidak terdeteksi.
2. Karena ada banyak section, kita perlu memastikan bahwa kita memprotect shared object di setiap section. Hal ini melanggar prinsip DRY (Dont Repeat Yourself).
3. Semakin besar scope yang mengakses shared object, semakin sulit bug untuk dideteksi.

### Corollary: Copy Data
Cara terbaik untuk menghindari masalah yang disebabkan oleh shared data adalah tidak menerapkannya. Kadang ada beberapa case dimana kita bisa menggunakan copy dari object/data, daripada membuat data tersebut menjadi *shared object*.

### Corollary: Thread Harus Seindependen Mungkin
Thread yang tidak memiliki shared object, hanya menggunakan local variable, hal ini sangat direkomendasikan karena dapat menghindari masalah yang disebabkan synchronization di atas.

## Kenali Librarymu
Disini menjelaskan soal library dari Java. Jadi, skip ya hehe.. :pray:

## Kenali Model Ekesekusi Concurrencymu
Ada beberapa model/cara kerja concurrency. Tapi sebelum ke sana, Ada beberapa definisi dalam concurrency yang perlu kita ketahui:
1. **Bound Resource:** Resource yang sudah fixed dan digunakan di environment yang berjalan secara concurrent. Contoh: Koneksi DB.
2. **Mutual Exclusion:** Hanya 1 thread yang bisa akses shared data source dalam 1 waktu.
3. **Starvation:** 1 atau lebih thread dilarang untuk menjalankan proses yang terlalu lama atau berjalan selamanya. Contoh: ada 2 thread, thread 1 berjalan sangat cepat tapi tidak berhenti. Sedangkan thread 2 berjalan lambat. Maka, thread 1 akan membuat thread 2 tidak akan berjalan.
4. **Deadlock:** Dua atau lebih thread saling menunggu untuk selesai. Misal thread A menunggu proses thread B selesai, baru bisa selesai. Sedangkan thread B menunggu proses thread A selesai, baru bisa selesai. Hal ini akan menyebabkan **Deadlock**.
5. **Livelock:** Thread berjalan, tapi di tengah jalan, dia gagal. Akhirnya, mengulang proses thread dari awal. Hal ini berjalan terus-menerus, bahkan selamanya. Contoh pada konsep producer-consumer. Dimana consumer gagal memroses pesan dan pesan dikirim kembali ke queue, lalu diterima lagi oleh consumer hanya untuk kembali gagal dan dikirim kembali ke queue.

setelah memahami hal di atas, kita bisa lanjut ke bawah.

### Producer-Consumer
Producer thread mengirim data ke dalam sebuah antrian (*queue*). Consumer thread mengambil data dari queue. 

Producer tidak akan mengirim queue baru jika queue penuh, consumer tidak akan mengambil data dari queue jika queue kosong.

keduanya saling mengirim sinyal. Producer mengirim sinyal bahwa queue tidak lagi kosong, sehingga consumer bisa memulai mengambil data dari queue. Consumer mengirim sinyal bahwa queue tidak lagi penuh, sehingga producer bisa lanjut mengirim data.

### Readers-Writers
Misal ada shared resources yang diakses oleh 2 thread, writers yang bertugas mengupdate shared resources dan readers yang mengambil data shared resources.

Tantangan dalam model ini adalah kapan kita harus mengupdate dan kapan kita harus membaca data. Terlalu sering update akan membuat reader selalu menunggu, karena shared resource sedang diakses writer. Terlalu sering dibaca, membuat writer tidak bisa mengakses shared resource, karena data sedang digunakan oleh thread readers.

### Dining Philosopher
Bayangkan beberapa orang filosof duduk dalam meja bundar. Para filosof akan selalu berpikir, kecuali ketika mereka lapar. Di tengah meja bundar terdapat sebuah mangkuk mie besar. Setiap filosof memiliki 1 batang sumpit yang diletakkan di sebelah kiri mereka. Seorang filosof tidak akan bisa makan kecuali mereka menggunakan 2 sumpit yang ada di kanan dan kiri mereka. Jika sumpit di kanan/kiri mereka sedang dipakai oleh filosof lain, maka dia harus menunggu sampai filosof lain itu selesai menggunakan sumpit tersebut.

Sekarang, ganti filosof dengan thread dan ganti sumpit dengan resource, maka hal ini sama dengan permasalahan yang dihadapi oleh aplikasi enterprise yang mana beberapa process saling berkompetisi memperebutkan resource. Hal ini jika tidak didesign dengan baik, akan menyebabkan berbagai masalah concurrency seperti deadlock, livelock, throughput, dan penurunan efisiensi.

## Jaga agar Sinkronisasi Tetap Kecil
Kalo di Golang, bisanya menggunakan mutex Lock atau semacamnya. Mutex Lock memastikan bahwa hanya ada 1 thread yang mengakses data di dalam code yang di-*lock*. Biasanya hal ini dilakukan ketika kita melakukan proses yang kritikal. *Locking* ini jelas menurunkan performa concurrency. Jadi, pastikan sedikit kode kritikal dalam *lock* yang kita buat.

## Membuat kode shut-down itu tidak mudah
Membuat kode yang harus tetap jalan itu berbeda dengan membuat kode yang jalan untuk beberapa saat, lalu di-*shutdown*.

Bayangkan sebuah parent thread yang memiliki beberapa child threads dan parent thread menunggu semua child thread selesai berjalan sebelum melakukan graceful shutdown. Bagaimana jika salahsatu child thread mati? Parent thread akan terus menunggu return value child thread tersebut dan graceful shutdown tidak akan terjadi.

Jadi, jika kita perlu untuk membuat kode concurrency yang terdapat graceful shutdown di dalamnya, luangkan waktu lebih banyak untuk membuat shutdown sistem selalu terjadi dengan benar.

## Testing Threaded Code
Membuktikan bahwa kode yang kita tulis itu benar = tidak berguna. Testing tidak membuktikan bahwa kode kita benar, tapi meminimalisir risiko. Hal ini benar dalam kode single-threaded. Ketika berurusan dengan kode multi-threaded, semua menjadi lebih kompleks dari sebelumnya.

Tips membuat threaded code
1. Anggap Error yang jarang terjadi sebagai masalah (Jangan dibiarkan). 
2. Pastikan Kode non-threading bekerja lebih dulu. Jangan mencari bug di kode yang tidak pake threading dan pakai threading secara bersamaan.
3. Buat kode threading kalian bisa diatur sehingga ia bisa berjalan sesuai konfigurasi. Misal berjalan di 1 thread, beberapa thread, berjalan secara lambat, cepat, dll.
4. Jalankan kode dalam beberapa environment. Bisa jadi di Windows berhasil, tapi di OS X dia gagal.
5. Jalankan kode agar gagal/mengatur bagian mana yang harus jalan dahulu. Bisa secara manual dengan memberi `sleep()`, atau secara automated menggunakan tools/library.