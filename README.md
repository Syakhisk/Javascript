# Javasript

# Content Navigation

![TOC](https://i.ibb.co/1vPQfZQ/gh-toc.gif)

# Node.js?
> Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code outside a web browser. Node.js lets developers use JavaScript to write command line tools and for server-side scripting—running scripts server-side to produce dynamic web page content before the page is sent to the user's web browser. Consequently, Node.js represents a "JavaScript everywhere" paradigm, unifying web-application development around a single programming language, rather than different languages for server-side and client-side scripts. 

**Intinya**, `Node.js` itu bisa membuat script `js` bisa di run selain di browser (CLI, Server, dsb). Sekarang kita gak bakal bahas itu.


# How to get help && How to help yourself
## Docs
MDN - [https://developer.mozilla.org/en-US/docs/](https://developer.mozilla.org/en-US/docs/) (good)

Kadang kalo kita cari sesuatu di `w3school` itu gak detail, contohnya kurang, dsb. Kalo di MDN semua lebih jelas dan bahkan bakal ada live preview-nya.

[Cara baca documentation syntax definition](http://cassandrawilcox.me/beginners-guide-developer-documentation/#anamesyntaxaunderstandingsyntaxdefinitions)
## Browser Console && `console.log("disini")`
Masalah paling sering muncul ketika ngoding in general adalah _"kenapa ini gak jalan"_. Di javascript kita bisa dengan mudah melakukan debugging karena fungsi `console.log` ini, dan ketika kalo memang ada sesuatu yang tidak diinginkan terjadi kita bisa langsung cek di Browser console, disitu ~~harusnya~~ bakal ada error apa yang terjadi (kecuali logical error). Selain `console.log`, javascript juga method `console` lain seperti `console.table`, `console.info`, `console.warn`, `console.time`

Contoh error:
![Contoh error](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5375d691e4b0d833740d56cc/images/5654429ec697915b26a59e55/file-AXo7oqC7R3.png)
Output console:
![output console](https://media.geeksforgeeks.org/wp-content/uploads/20190305110510/Screenshot-1621-e1551764124897.png)

Read more [di sini](https://developer.mozilla.org/en-US/docs/Web/API/console)

# How to run

## As a Script
Javascript (seperti kodrat nya) bisa dijalankan di browser, untuk file extensi nya itu bisa di `.js`, `.mjs`, atau script tag di `.html`.

## Browser Console
Chrome Based - `CTRL+SHIFT+J`

Firefox Based - `CTRL+SHIFT+K`

## Node.js REPL
`$ node`

`$ node [filename]`

# First-class function
Javascript merupakan bahasa yang menerapkan __first-class function__ yang dimana artinya sebuah __function__ diperlakukan __sama dengan variable__. Jadi didalam javacript, sebuah function itu bisa dijadikan: argument, return value, dan value dari variable lain.

Contoh:
```js
const m42nk = function() {
   console.log("geming");
}
m42nk(); // geming
```
```js
function sayGeming() {
   return "geming, ";
}
function greeting(gemingMessage, name) {
  console.log(sayGeming() + name);
}
greeting(sayGeming, "m42nk!"); // Hello, m42nk!
```
```js
function sayGeming() {
   return function() {
      console.log("GeEmiNg!");
   }
}
sayGeming()(); // GeEmiNg! 
```

# Semicolons

Di javascript itu bebas mau dikasih semicolon (titik koma) atau engga di akhir setiap statement, kecuali di beberapa keadaan ([iife](https://developer.mozilla.org/en-US/docs/Glossary/IIFE))

```js

const nama_asli = "Syakhisk"; // bisa

const nama_panggung = "m42nk" // boleh

```

# Variables && Scopes
> var? let? const?

Di javascript, ada 3 cara untuk membuat variable, yaitu pake `var`, `let`, atau `const`. Masing-masing cara punya perbedaan.

## `var`
> Declares a variable, optionally initializing it to a value.

## `let`
> Declares a block-scoped, local variable, optionally initializing it to a value.

## `const`
> Declares a block-scoped, read-only named constant.

Read more [di sini](https://hackernoon.com/js-var-let-or-const-67e51dbb716f) dan [di situ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types)

# Functions
## Usage

Cara mendeklarasikan function di javascript ini mirip dengan kebanyakan bahasa lain, tapi ada beberapa yang buat unik.

```js
// Biasa - function declaration
function geming(){
  console.log("halo")
}

// Anonymous (untuk callback, argument, atau iife)
function (){
  console.log("aku gapunya nama")
}

// Taro di variable - function expression
const password = function () {
  return "verysecret123andri"
}

password() // verysecret123andri

```

## Arrow Function

```js
const sixninefortwenty = () => "nice" // nice

// Artinya sama kaya
const sixninefortwenty = function() {
  return "nice"
}  

console.log(sixninefortwenty()) // nice

// Atau
const sebutNamakuTigaKali = (nama) => {
  for(let i = 0; i < 3; i++){
    console.log(nama)
  }
}

sebutNamakuTigaKali("andri") 
// andri
// andri
// andri
```

## Arguments && Parameters
### Default value
Default value dari argument (parameter) akan digunakan apabila argument tersebut tidak diberikan pada saat pemanggilan function.

Contoh:
```js
const tambahinDong = (val1, val2 = 0) => val1 + val2;

const x = tambahinDong(99) // 99
const y = tambahinDong(99, 321) // 420
```

### Rest Parameters - variadic funcitons
Jadi sebuah function dapat memiliki jumlah variable yang indefinite dengan cara menggunakan triple-dots atau `...`, dimana nanti akan disimpan sebagai array didalam scope function tersebut.

Contoh:
```js
function numbah(...num){
 console.log(num)
}

numbah(68,419,0) // [ 68, 419, 0 ]
```

Read more [di sini](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)

Kita juga bisa menjadikan semua tipe variable sebagai arguments (object, function, number, etc).

Contoh:
```js
// Array
function tambahinDong(arr){
  let sum = 0;
  
  for(let i; i < arr.length; i++) {
    sum += arr[i]
  }
  
  return sum
  
  // atau cara magic (sama-sama jumlahin semua value)
  // return arr.reduce((prev, current) => prev + current);
}

const nilaiku = [6, 5, 3, 7, 1, 0]

console.log(tambahinDong(nilaiku)) // 22 (gak lulus 😢)
```

# Objects

> JavaScript is designed on a simple object-based paradigm. An object is a collection of properties, and a property is an association between a name (or key) and a value. A property's value can be a function, in which case the property is known as a method.

__Intinya__, `object` dalam javascript itu sebuah koleksi yang isinya `key-value` pair. Mungkin di __python__ ini bisa disebut `dictionary`, dan di __php__ disebut `associative array`.

## Usage
```js
// definition and assignment
const mhs = new Object();
mhs.nama_depan = "Lorem"
mhs.nama_belakang = "Ipsum"
mhs.nrp = "05312140000001"
mhs.getNama = function () {
  // pakai template string, diawali pake backtick (`)
  // bisa akses js expression dengan cara 
  // pake ${expression}
  return `${this.nama_depan} ${this.nama_belakang}`
}

console.log(mhs.getNama()) // Lorem Ipsum

// shorthand

const mhs = {
  nama_depan: "Lorem",
  nama_belakang: "Ipsum",
  nrp: "05312140000001",
  getNamaArrow: () => `${this.nama_depan} ${this.nama_belakang}`,
  getNama: function() {
      return `${this.nama_depan} ${this.nama_belakang}`
    } 
}

console.log(mhs.nama_depan) // Lorem
console.log(mhs["nama_belakang"]) // Ipsum
console.log(mhs.getNamaArrow()) // undefined undefined
console.log(mhs.getNama()) // Lorem Ipsum
```

# Array

Seperti pada umumnya, array merupakan sebuah object yang mirip seperti list yang biasa kita akses menggunakan index `arr[0], arr[1], etc`. 

Javascript menerapkan __zero-based indexing__ yang artinya index dari array dimulai dari 0. Array di javascript juga tidak memiliki fixed-length, dan tidak mengharuskan semua elemen di dalamnya memiliki tipe data yang sama.

## Usage
```js
const arr1 = [] // deklarasi
const arr2 = [1,2,3] // deklarasi + inisialisasi
const arr3 = new Array() // menggunakan kelas array

const arr4 = [
  1, 
  "dua", 
  3.0, 
  {num: 4}, 
  function(){return 5},
  () => 6,
  [7],
]; // elemen berbeda tipe
```

## Methods

Methods dari class array ini lumayan banyak, salah satu method yang biasa digunakan itu: `push`, `pop`, `map`, `filter`, `reduce`, `find`, `includes`, `join`, dsb.

Contoh:
```js
const arr = [10, 9];
arr.push(2); // arr = [10, 9, 2] -- menambahkan elemen kedalam array

const val1 = arr.pop(); // val1 = 2, arr = [10, 9] -- mengeluarkan elemen terakhir

const val2 = arr.shift(); // val2 = 10, arr = [9] -- mengeluarkan elemen pertama

// filter dan map akan mereturn array baru tanpa mengubah array asli
const arr2 = [1,2,3,4,5]
const genap = arr.filter((num) => num % 2) // genap = [2,4]
const tambah10 = arr.map((num) => num + 10 ) // tambah10 = [11,12,13,14,15]
console.log(arr2) // [1,2,3,4,5]

const nama = ["lorem", "ipsum"];
console.log(nama.join()) // "lorem,ipsum"
console.log(nama.join(" ")) // "lorem ipsum"
```

Read more [di sini](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

# Destructuring

> The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

__Intinya__, destructuring itu bisa "mengekspos" isi dari sesuatu (object/array) menjadi variable sendiri.

Contoh:
```js
// array destructuring, sesuai index
const nama = ["lorem", "ipsum"]
const [namaDepan, namaBelakang] = nama

console.log(namaDepan) // "lorem"
console.log(namaBelakang) // "ipsum"

// object destructuring, sesuai key
const mhs = {
  nama = "foobar",
  password = "verysecret123andri"
  nrp = "05311940000003"
}

const {nama, nrp} = mhs;

console.log(nama) // "foobar"
console.log(nrp) // "05311940000003"


// rest assignment
const halo = ["halo", "bandung", "ibu", "kota"]
const [kata_pertama, ...kata_sisanya] = halo

console.log(kata_pertama) // "halo" -- string
console.log(kata_sisanya) // ["bandung", "ibu", "kota"] -- array
```

Read more [di sini](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

# Equality

Semakin kalian belajar javascript semakin kalian tau seberapa aneh `equality` di dalamnya. Tapi sekarang, intinya yang paling sering bikin bingung itu perbedaan `==` dengan `===`. triple-equal artinya strict-equality dimana tipe data dari value yang dibandingkan harus sama.

Contoh:
```js
// equality
console.log(1 == 1) // true
console.log(1 == "1") // true
console.log(1 == true) // true
console.log(0 == false) // true

console.log(1 === 1) // true
console.log(1 === "1") // false
console.log(1 === true) // false
console.log(0 === false) // false

```

# Notes
Feel free to submit an issue if there are any incorrect information here.


# References
https://developer.mozilla.org/en-US/docs/

https://learnxinyminutes.com/docs/javascript/

https://hackernoon.com/js-var-let-or-const-67e51dbb716f

https://en.wikipedia.org/wiki/Node.js

