# Hasil Maksimal, Usaha Minimal dengan ES6

Sebuah _summary_ yang ditulis oleh :

-   **Nama :** Ahmad Yogi
-   **Program :** _React and React Native for Front-end Developer_
-   **Kode Peserta :** RCTN-KS03-008

## Apa itu ES6?

ES6, atau juga dikenal sebagai _ECMAScript 6_ adalah sebuah standar untuk bahasa Pemrograman _JavaScript_. ES6 digunakan untuk melakukan standarisasi bagaimana _JavaScript_ bekerja seperti mendefinisikan suatu variabel, penulisan kode dengan sintaksis yang sesuai dan lain sebagainya. ES6 mempermudah _developer_ untuk menuliskan kode karena hanya dengan sintaks yang **minimal** dapat menghasilkan sesuatu yang **maksimal**.

## Pendeklarasian Variabel

Pada ES6, kita dapat mendeklarasikan variabel dengan menggunakan _keyword_ `let` dan `const`.

### let

_Keyword_ `let` memungkinan kita untuk mendeklarasikan sebuah variabel yang "_scope_"(cakupan)-nya hanya pada blok kode saja (_**block scope**_). Dengan kata lain, jika variabel dideklarasikan pada suatu blok kode, maka hanya pada blok kode itu saja variabel tersebut dapat diakses.

Contoh :

```js
var x = 10;
console.log(x);

{
    let x = 6;
    console.log(x);
}
console.log(x);

// output:
// >> 10
// >> 6
// >> 10
```

## const

Mirip seperti _keyword_ `let`, _keyword_ `const` digunakan untuk mendeklarasikan suatu variabel yang bersifat _**block scope**_, hanya saja _keyword_ ini menyebabkan variabel menjadi _read only_ atau hanya dapat dibaca saja, dengan kata lain kita tidak bisa mengganti _value_ pada variabel tersebut.

Contoh :

```js
var x = 19;
console.log(x);

{
    const x = 45;
    console.log(x);
    x = 65; // <= akan terjadi error!
}

// output:
// >> 19
// >> 45
// >> TypeError: Assignment to constant variable.
```

## Arrow Function

_Arrow function_ adalah sebuah fitur baru pada ES6 yang digunakan untuk menyederhanakan penulisan _function_ pada _Javascript_. _Arrow function_ ditandai dengan simbol `=>`. _Arrow function_ memiliki fitur _implicit return_, yakni kita tidak perlu lagi menuliskan _keyword_ `return` dan tanda kurung `{}` jika _function_ hanya berupa satu baris.

Contoh :

```js
// penulisan gaya lama
function add(a, b) {
    return a + b;
}

// penulisan gaya baru (arrow function)
const add = (a, b) => a + b;

// cara pemanggilan tetap sama
add(12, 5);
```

> **Catatan:** _Arrow function_ bukan dimaksudkan untuk menggantikan _function_ biasa.

## This

### Pengunaan _this_

_Keyword_ `this` digunakan untuk mereferensikan _object_. _Object_ di sini tergantung dari bagaimana kita menggunakan _keyword this_.

-   Pada _method_ dalam _object_, _this_ adalah _object_ itu sendiri.
-   Di luar _scope_ (global), _this_ adalah _global object_.
-   Pada _function_, _this_ adalah _global object_.
-   Pada _function_ dengan mode _strict_, _this_ menjadi _undefined_.
-   Pada _event_, _this_ adalah _element_ yang sedang menerima _event_.

Contoh :

```js
// this dalam method object
const person = {
    name: "Ahmad Yogi",
    talk() {
        console.log(this.name);
    },
};

// this dalam function
function sayThis() {
    return this;
}
```

### Bind _this_

Pada _method_ dalam _object_, _this_ adalah _object_ itu sendiri. Namun jika _method_ tersebut kita _assign_ ke suatu variabel dan kemudian variabel tersebut kita panggil, maka _this_ menjadi _global object_. Agar _this_ tetap _object_ dari _method_, kita dapat menggunakan _function_ `bind`.

Contoh :

```js
const person = {
    name: "Yana",
    talk() {
        console.log(this.name);
    },
};

const talk = person.talk;
const talkBind = person.talk.bind(person);

talk();
talkBind();

// output:
// >> undefined
// >> Yana
```

## Default Parameters

Pada ES6, kita dapat memberikan suatu nilai _default_ pada parameter dari sebuah _function_ yang memiliki parameter jika _function_ tersebut dipanggil dengan parameter kosong.

Contoh :

```js
const increment = (num, inc = 1) => num + inc;

// parameter inc diisi
console.log(increment(2, 2));

// parameter inc tidak diisi
console.log(increment(2));

// output :
// >> 4
// >> 3
```

## Template Literals

ES6 menyediakan fitur _template literals_, yakni untuk memberikan "templat" pada suatu data _string_ yang dapat diisikan dengan kode-kode valid _JavaScript_. _Template literals_ biasanya digunakan untuk membuat _string_ multi-baris, interpolasi _string_, _tagged templates_ dan lain-lain.

Contoh interpolasi _string_ :

```js
let name = "Yana";
let message = `Halo, nama saya ${name}`;

console.log(message);

// output :
// >> Halo, nama saya Yana
```

Contoh _string_ multi-baris :

```js
let message = `Ini adalah string
    dengan multi-baris,
    sangat cocok untuk menulis
    pesan.`;

console.log(message);

// output :
// >> Ini adalah string
//    dengan multi-baris,
//    sangat cocok untuk menulis
//    pesan.
```

Contoh _tagged templates_ :

```js
let name = "Yana";
let country = "Rusia";

const printMsg = (str, name, country) => {
    // str berupa array
    let str0 = str[0]; // <= "Halo, saya "
    let str1 = str[1]; // <= " dari "

    console.log(`${str0}${name}${str1}${country}`);
};

printMsg`Halo, saya ${name} dari ${country}`;

// output :
// >> Halo, saya Yana dari Rusia
```

## Operator Spread dan Rest

ES6 memberikan sebuah fitur baru yakni operator _spread_ dan _rest_, ditulis menggunakan simbol tiga buah titik `...` yang memiliki perbedaan pada pengunaannya.

### Spread

Operator _spread_ memungkinkan sebuah data yang dapat diiterasi (disebut _iterable_) seperti _array_ atau _string_ tiap-tiap elemennya dipecah kemudian disebarkan menjadi tiap-tiap parameter pada sebuah _function_.

Contoh :

```js
const add = (a, b, c) => a + b + c;
const nums = [1, 2, 3];

console.log(add(...nums));

// output :
// >> 6
```

Operator _spread_ juga memungkinkan kita untuk menggabungkan sebuah data _iterable_ dengan data _iterable_ lainnya menjadi sebuah satu kesatuan.

Contoh :

```js
const arr = [1, 2, 3];

console.log([arr, 4, 5, 6]); // <= arr menjadi elemen
console.log([...arr, 4, 5, 6]); // <= tiap elemen arr menjadi elemen baru

// output :
// >> [[1, 2, 3], 4, 5, 6]
// >> [1, 2, 3, 4, 5, 6]
```

### Rest

Operator _rest_ dapat digunakan pada _function_ sebagai sebuah parameter dengan tujuan untuk mengkumpulkan semua parameter yang dimasukan menjadi satu kesatuan (dalam bentuk _array_).

Contoh :

```js
const displayNames = (...names) => console.log(names);

displayNames("Google", "DuckDuckGo", "Bing", "Yandex");

// output :
// >> [ 'Google', 'DuckDuckGo', 'Bing', 'Yandex' ]
```

## Destructuring

_Destructuring_ adalah sebuah fitur pada ES6 yang memungkinkan kita untuk memecah elemen-elemen dari data _iterable_ seperti _array_ ataupun _object_ menjadi bagian-bagian kecil (elemen-elemen menjadi variabel yang terpisah).

Contoh penerapan pada _array_ :

```js
// penerapan pada array
const operatingSystems = ["Windows", "Linux", "MacOS", "Android", "Chrome OS"];
const [firstElement, secondElement, , fourthElement] = operatingSystems;

console.log(`Elemen pertama: ${firstElement}`);
console.log(`Elemen kedua: ${secondElement}`);
console.log(`Elemen keempat: ${fourthElement}`);

// output:
// >> Elemen pertama: Windows
// >> Elemen kedua: Linux
// >> Elemen keempat: Android
```

Contoh penerapan pada _object_ :

```js
// penerapan pada object
const user = {
    userName: "ahmadyogi543",
    password: "verystrongpasswd",
    spouse: "Yana",
    children: 2,
};

const { userName, spouse, children } = user;

console.log(`Username: ${userName}`);
console.log(`Spouse: ${spouse}`);
console.log(`No of children: ${children}`);

// output:
// >> Username: ahmadyogi543
// >> Spouse: Yana
// >> No of children: 2
```

## Array Methods

ES6 memudahkan kita bekerja dengan _array_. Pada ES6 terdapat beberapa _helper function_ (atau lebih tepatnya disebut sebagai _method_) yang dapat mempermudah kita dalam memproses elemen-elemen pada _array_.

### For Each

_Method_ _forEach_ pada _JavaScript_ digunakan untuk memproses tiap-tiap elemen pada _array_ dengan sebuah _function_ yang diberikan sebagai sebuah parameter. _Method_ ini tidak mengembalikan nilai apapun.

Contoh :

```js
const fishes = ["Nila", "Patin", "Haruan"];

fishes.forEach((fish) => {
    fish = fish + " goreng";
    console.log(fish);
});

// output :
// >> Nila goreng
// >> Patin goreng
// >> Haruan goreng
```

### Map

_Mehod_ map pada JavaScript digunakan memetakan suatu _function_ pada tiap elemen pada _array_ untuk menghasilkan sebuah _array_ baru hasil dari proses pemetaan.

Contoh :

```js
const nums = [1, 2, 3, 4, 5];
const newNums = nums.map((num) => num + 2);

console.log(newNums);

// output :
// >> [ 3, 4, 5, 6, 7 ]
```

### Filter

Mirip seperti _method_ forEach, filter juga memproses tiap-tiap elemen pada _array_ dengan sebuah _function_ namun _function_ pada filter berupa sebuah perkondisian. Tiap-tiap elemen akan dites apakah sesuai dengan kondisi yang sudah ditentukan atau tidak. Jika sesuai maka elemen akan masuk ke _array_ baru berupa hasil proses _filtering_.

Contoh :

```js
const nums = [1, 2, 3, 4, 5, 6];
const evenNums = nums.filter((num) => num % 2 === 0);

console.log(evenNums);

// output:
// >> [ 2, 4, 6 ]
```

### Find

_Method_ find pada _array_ digunakan untuk mencari sebuah nilai yang sesuai dengan kriteria yang diberikan oleh sebuah _function_ yang menjadi parameter dari _method_ find. Jika terdapat lebih dari satu elemen yang memenuhi kriteria _function_, _method_ hanya akan mengembalikan elemen yang pertama kali lulus pada kritera _function_.

Contoh :

```js
const nums = [45, 12, 613, 136, 116, 1241];
const found = nums.find((num) => num > 100);

console.log(found);

// output :
// >> 613
```

### Every dan Some

Method every dan some digunakan untuk memberikan "pertanyaan" kepada _array_ (berupa _function_ perkondisian) yang nantinya akan menghasilkan sebuah nilai _boolean_. Bedanya every dan some adalah untuk every akan memberikan jawaban `true` jika semua elemen pada _array_ memenuhi hasil tes, sedangkan untuk some akan memberikan jawaban `true` jika ada beberapa elemen yang memenuhi hasil tes.

Contoh penerapan _every_:

```js
// penerapan every
const names = ["Yogi", "Yana", "Yelena", "Yohana"];

const isEveryStartsWithY = names.every((name) => name[0] === "Y");
console.log(isEveryStartsWithY);

// output :
// >> true
```

Contoh penerapan _some_ :

```js
// penerapan some
const names = ["Yogi", "Yana", "Eren", "Yohana"];

const isAnyStartsWithE = names.some((name) => name[0] === "E");
console.log(isAnyStartsWithE);

// output :
// >> true
```

### Reduce

_Method_ reduce mengeksekusi sebuah parameter _function_, disebut sebagai _reducer_ yang dapat mengakses tiap-tiap elemen secara berurutan serta juga elemen sebelum elemen yang sedang diakses untuk melakukan suatu proses pada elemen _array_. Reduce juga meminta sebuah parameter untuk nilai awal karena ketika elemen pada _array_ pertama kali diakses, elemen sebelumnya tidak ada, maka dari itu nilai awal dijadikan sebagai elemen sebelum elemen pertama yang diakses. _Method_ ini menghasilkan sebuah nilai.

Contoh :

```js
const nums = [1, 2, 3, 4, 5];
const sumOfNums = nums.reduce((pre, curr) => pre + curr, 0);
const sumOfNumsStartWith5 = nums.reduce((pre, curr) => pre + curr, 5);

console.log(sumOfNums);
console.log(sumOfNumsStartWith5);

// output :
// >> 15
// >> 20
```

## Modules ES6

Pada ES6 terdapat fitur _modules_ yang digunakan untuk memecah kode program yang besar menjadi bagian-bagian kecil dalam _file_ (disebut sebagai _module_) yang berbeda. Hal ini dilakukan agar kode program lebih mudah di-_maintain_.

Modules dapat dimasukan (_import_) ke dalam _module_ lain untuk digunakan maupun dikeluarkan (_export_) untuk digunakan pada _module_ lain.

### Export

Kita dapat mengeluarkan (_export_) suatu _class_, _function_, ataupun variabel dari suatu _module_ ke _module_ lain pada JavaScript dengan menggunakan _keyword_ `export` atau `export default`.

Contoh :

```js
// export satu persatu
export const PI = 3.1415926;
export const E = 2.17828184;

// export secara bersamaan
const PI = 3.1415926;
const E = 2.17828184;

export { PI, E };
```

```js
// export default
const square = (n) => n * n;
export default square;
```

### Import

Kita dapat memasukan (_import_) hasil _export_ dari suatu _module_ ke _module_ lain agar dapat digunakan pada _module_ yang sedang melakukan _import_. Terdapat dua cara untuk meng-_import_ _module_ yakni sebagai berikut.

```js
// import sesuai nama yang diexport
import { PI, E, square } from "./maths.js";

// import dari default export
import square from "./square.js";
```

## Class

Suatu fitur penting yang ditambahkan pada ES6 adalah _class_. Dengan adanya _class_, kita dapat menerapkan model pemrograman berorientasi objek pada JavaScript. Pada _class_ terdapat istilah atribut, dan _method_.

Contoh penulisan _class_ pada ES6 :

```js
class Person {
    // isi dari class
}
```

Contoh instansiasi objek _class_ pada ES6 :

```js
const person = new Person();
```

### Constructor

_Constructor_ adalah suatu _method_ khusus yang akan terpanggil ketika kita melakukan instansiasi objek untuk _class_ tersebut sehingga _constructor_ berguna untuk mengatur nilai awal dari suatu atribut ataupun hal yang lainnya.

Contoh penulisan _constructor_ pada ES6 :

```js
class Person {
    // constructor ditulis di sini
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
}
```

### Methods

_Method_ pada _class_ ES6 digunakan untuk memberikan fungsionalitas pada suatu objek dari _class_ tersebut.

Contoh :

```js
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    // method bernama sayHi
    sayHi() {
        console.log("Hi there");
    }
}

// instansiasi objek
const person = new Person("Matoi", "Ryuko");

// method dipanggil
person.sayHi();

// output :
// >> Hi there
```

### Sub Class

Sederhananya _sub class_ adalah sebuah _class_ yang mewarisi semua atribut dan _method_ yang terdapat pada _ main class_ (sering disebut sebagai _parent class_). Digunakan untuk memberikan suatu tambahan tanpa menghilangkan dasar dari _main class_ sehingga _main class_ dapat diwarisi ke _sub class_ lain yang berbeda.

_Keyword_ yang digunakan adalah `extends` dan `super`.

Contoh :

```js
// main class (parent)
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    sayHi() {
        console.log("Hi there");
    }
}

// sub class
class Student extends Person {
    constructor(name, age) {
        super(name, age);
    }

    sayHi() {
        console.log("Hi there, I am a student");
    }
}
```

> **Catatan:** super digunakan pada _constructor sub class_ agar _sub class_ dapat mengakses semua hal yang ada pada _main class_.

## Array API

Array pada JavaScript adalah sebuah objek. Tentunya objek memiliki _method_. Kita dapat berinteraksi lebih dekat lagi dengan _array pada JavaScript_ (pada level _array_ sebagai _object_) dengan menggunakan API _Array_.

### Array.from

_Method static_ `Array.from()` digunakan untuk membuat _instance_ _array_ pada level _object_ dari suatu _object_ mirip _array_ (_array-like_) yang dapat diiterasi.

Contoh :

```js
console.log(Array.from("wow"));
console.log(Array.from([1, 2, 3], (x) => x + x));

// output:
// >> Array ["w", "o", "w"]
// >> Array [2, 4, 6]
```

### Array.copyWithin

_Method static_ `Array.copyWithin()` digunakan untuk menyalin suatu elemen pada _array_ ke elemen lain pada _array_ tersebut juga, maka dari itu nama _method_-nya `copyWithin`.

Contoh :

```js
const alphabets = ["a", "b", "c", "d", "e"];

// menyalin elemen index 3 ke elemen index 0
console.log(alphabets.copyWithin(0, 3, 4));

// menyalin elemen index 3 dan seterusnya ke index 1 dan seterusnya
console.log(alphabets.copyWithin(1, 3));

// output:
// >> Array ["d", "b", "c", "d", "e"]
// >> Array ["d", "d", "e", "d", "e"]
```

### Array.prototype.fill

_Method_ ini digunakan untuk mengganti semua nilai pada elemen _array_ mulai dari _index_ awal (_default-nya 0) hingga ke \_index_ akhir (\_default-nya `array.length`).

Contoh :

```js
const nums = [1, 2, 3, 4];

// mengisi nilai 0 pada semua elemen array
// dimulai dari index 2 sampai index 4
console.log(nums.fill(0, 2, 4));

// mengisi nilai 5 pada semua elemen array
// dimulai dari index 1
console.log(nums.fill(5, 1));

// mengisi nilai 6 pada semua elemen array
console.log(nums.fill(6));

// output :
// >> [1, 2, 0, 0]
// >> [1, 5, 5, 5]
// >> [6, 6, 6, 6]
```

### Array.prototype.find

_Method_ ini akan mengembalikan elemen pertama pada _array_ yang berhasil lulus pada _function_ uji coba, jika tidak ada elemen yang berhasil lulus, nilai `undefined` akan dikembalikan.

Contoh :

```js
const nums = [5, 12, 8, 130, 44];
const found = nums.find((element) => element > 10);

console.log(found);

// output:
// >> 12
```

### Array.prototype.values

_Method_ ini digunakan untuk mengembalikan semua nilai dari _array_ sebagai **_Array Iterator_** yang dapat diiterasi dengan menggunakan _keyword_ `of`.

Contoh :

```js
const nums = [1, 3, 5];
const iterator = nums.values();

for (const value of iterator) {
    console.log(value);
}

// output:
// 1
// 3
// 5
```

### Array.prototype.keys

_Method_ ini akan mengembalikan sebuah _Array Iterator\_\_ yang berisikan \_key_ untuk tiap elemen pada _array_.

Contoh :

```js
const nums = [1, 3, 5];
const iterator = nums.keys();

for (const value of iterator) {
    console.log(value);
}

// output:
// 0
// 1
// 2
```

### Array.prototype.entries

_Method_ ini digunakan untuk mengambil _key_ dan _value_ pada tiap elemen _array_ dan menyimpannya pada sebuah _Array Iterator_.

Contoh :

```js
const nums = [1, 3, 5];
const entries = nums.entries();

for (const entry of entries) {
    console.log(entry);
}

// output:
// [0, 1]
// [1, 3]
// [2, 5]
```

## Object API

Sama seperti _array_, kita juga dapat berinteraksi lebih dekat dengan _object_ pada JavaScript dengan menggunakan API _object_.

### Object.is

Digunakan untuk membandingkan dua buah nilai apakah bernilai sama atau tidak, mirip seperti operator `==` atau `===`, namun lebih **ketat** pemeriksaannya.

Contoh :

```js
const a = 0;
const b = -0;

console.log(a == b);
console.log(a === b);
console.log(Object.is(a, b));

// output:
// >> true
// >> true
// >> false
```

### Object.setPrototypeOf

Digunakan untuk memberikan suatu objek properti dari suatu objek lain.

Contoh :

```js
const person = {
    sayHi() {
        console.log("Hi");
    },
};

const student = {};

Object.setPrototypeOf(student, person);

// output:
// >> Hi
```
