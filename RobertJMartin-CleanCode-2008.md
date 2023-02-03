# Clean Code
A Handbook Of Agile Software Craftmanship

> **Note:**
> 
> Markdown ini berisi summary dari yg telah saya baca. Tidak semuanya saya tulis di sini. Jadi, tetap pertimbangkan untuk membaca langsung bukunya.

# Penamaan
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

## Interface dan Implementasinya
Biasanya kita mungkin akan menamai interface dengan nama, contoh `IConfiguration` dan `Configuration`. Akan lebih baik jika bernama tetap `Configuration` dan implementasinya dinamai `ConfigurationImplementation`.

## Class Name dan Method Name
Gunakan kata benda untuk Nama kelas.

Gunakan kata kerja untuk Nama Method.

## Gunakan 1 Kata per Konsep
Misal, untuk mengambil data dalam bentuk pagination, gunakan 1 kata saja, misal `Get`. Jangan ada frasa lain seperti `Fetch`, `Retrive`, dll.

Ketika ada logic lain, misal mengambil data tanpa pagination, kita bisa gunakan frasa lain (atau kata lain. Lihat *Jangan gunakan kata yang Ambigu*).

## Jangan gunakan kata yang Ambigu
Jika ngikut aturan 1 Kata per Konsep di atas, kita akan banyak menemukan kata yang sama seperti `Add...`. Usahakan berikan nama function yang tidak ambigu. Misal, `Add...` untuk menambahkan value ke objek, `Insert...` untuk menambahkan data ke DB.

## Use Solution Domain Names
## Use Problem Domain Names

## Berikan Konteks yg Jelas
variable `name, address, city` dalam function `InsertUserAddress` mungkin sudah jelas. Tapi bagaimana jika variable `city` sendirian di function `sendPackage`?

Lebih baik gunakan nama seperti `destinationCity`.

## Hati-hati dalam Memberikan Konteks
Misal kita kerja di perusahaan `XYZ`. Jangan menamai variable kita dengan `XYZusername`, `XYZConfiguration`, dll. Selain tidak informatif, ini juga memberikan prefix yang tidak perlu.

# Functions

## Kecil
Function harus kecil. Bagaimana menentukan apakah function itu kecil? Lanjut ke pembahasan berikutnya

### Block dan Indentasi
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