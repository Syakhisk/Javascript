# Javasript

# Content Navigation

![TOC](https://i.ibb.co/1vPQfZQ/gh-toc.gif)

# Node.js? Maybe later
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
# Objects

// TODO

# Functions
## Definition

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
sixninefortwenty() // nice

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

# Array Methods

// TODO

# Equality

// TODO

# Async - Await

// TODO

# Useful Notes

// TODO

# References
https://learnxinyminutes.com/docs/javascript/

https://hackernoon.com/js-var-let-or-const-67e51dbb716f

https://en.wikipedia.org/wiki/Node.js

https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function
