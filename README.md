# Modern Javascript

## 1. JavaScript Fat Arrow Functions
### Normal Function
```js
function number() {
    return 10;
}
console.log(number());
```
### Arrow Function
```js
const number = () => {
    return 10;
};
console.log(number());
```
### Arrow Function without return keyword
```js
const number = () => 10;
console.log(number());
```
### Arrow Function with console.log()
```js
const number = () => console.log(10);
number();
```
### Arrow Function with a parameter
```js
const number = n => n;
console.log(number(10));
```
### Arrow Function with two parameters
```js
const number = (a, b) => a + b;
console.log(number(10, 20));
```
### Arrow Function with brackets
```js
const number = (a, b) => {
    const sum = a + b;
    return sum;
};
```
### this confusion in normal function
```js
const javascript = {
    name: 'JavaScript',
    libraries: ["React", "Angular", "Vue"],
    printLibraries: function() {
        console.log(this);
        this.libraries.forEach(function(a) {
            console.log(this);
            console.log(`${this.name} loves ${a}`);
        });
    }
};
javascript.printLibraries();
```
### this confusion in normal function (solved)
```js
const javascript = {
    name: 'JavaScript',
    libraries: ["React", "Angular", "Vue"],
    printLibraries: function() {
        const self = this;
        this.libraries.forEach(function(a) {
            console.log(`${self.name} loves ${a}`);
        });
    }
};
javascript.printLibraries();
```
### this confusion solved in arrow function
```js
const javascript = {
    name: 'JavaScript',
    libraries: ["React", "Angular", "Vue"],
    printLibraries: function() {
        this.libraries.forEach((a) => console.log(`${this.name} loves ${a}`));
    }
};
javascript.printLibraries();
```
### this confusion in addEventListener function
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <input type="text" class="search" placeholder="type here">
    <p class="result"></p>
    <p class="thanks"></p>
    <script src="playground.js"></script>
</body>

</html>
```
```js
const searchInput = document.querySelector(".search");
const display = document.querySelector(".result");
const thanks = document.querySelector(".thanks");

function show() {
    display.innerHTML = this.value;
    /* setTimeout(function() {
        thanks.innerHTML = `You have typed: ${this.value}`;
    }, 1000); */
    setTimeout(() => {
        thanks.innerHTML = `You have typed: ${this.value}`;
    }, 1000);
}
searchInput.addEventListener("keyup", show);
```
### new keyword for arrow function
```js
const Person = (name) => { // Here, Person isn't a constructor function
    this.name = name;
};
const sakib = new Person('Sakib');
console.log(sakib.name);
```
### new keyword for normal function
```js
function Person(name) { // Here, Person is also a constructor function
    this.name = name;
}
const sakib = new Person('Sakib');
console.log(sakib.name);
```