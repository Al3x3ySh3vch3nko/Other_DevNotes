***
## Closoures замыкания 
***
автоматическое поведение JS при котором функция "запоминает" переменные в том месте откуда она была взята на момент ее вызова даже при том что в стэке нет выполняемых функций. 
(!) Функция имеет доступ ко всему выполняемому контексту в котором она была создана или с которым она связана(!) Даже если он был уже выполнен до этого.
Окружение для функции сохраняется в движке.

Замыкание имеет преимущество при выполнении в стэке
```
const secureBooking = function () {
  let passengerCount = 0;

  return function () {
    passengerCount++; \\ функция увеличивет переменную passengerCount в том виде, в котором она была при ее вызове, хотя эта переменная не в стэке
    console.log(`${passengerCount} passengers`);
  };
};

const booker = secureBooking(); \\ функция booker имеет доступ к переменным внутри функции secureBooking

booker(); \\ passengerCount = 1
booker(); \\ passengerCount = 2
booker(); \\ passengerCount = 3

console.dir(booker);
```
ПРИМЕР
```
let f;

const g = function () {
  const a = 23;
  f = function () {
    console.log(a * 2);
  };
};

const h = function () {
  const b = 777;
  f = function () {
    console.log(b * 2);
  };
};

g();
f();
console.dir(f);
```

Переназначение функции f
```
h();
f();
console.dir(f);
```

ПРИМЕР 2
```
const boardPassengers = function (n, wait) {
  const perGroup = n / 3;

  setTimeout(function () {
    console.log(`We are now boarding all ${n} passengers`);
    console.log(`There are 3 groups, each with ${perGroup} passengers`);
  }, wait * 1000);

  console.log(`Will start boarding in ${wait} seconds`);
};

const perGroup = 1000;
boardPassengers(180, 3);
```

Coding Challenge #2
/*
This is more of a thinking challenge than a coding challenge ??

Take the IIFE below and at the end of the function, attach an event listener that changes the color of the selected h1 element ('header') to blue, each time the BODY element is clicked. Do NOT select the h1 element again!

And now explain to YOURSELF (or someone around you) WHY this worked! Take all the time you need. Think about WHEN exactly the callback function is executed, and what that means for the variables involved in this example.

GOOD LUCK ??
*/

/*
(function ()
{
  const header = document.querySelector('h1');
  header.style.color = 'red';

  document.querySelector('body').addEventListener('click', function () {
    header.style.color = 'blue';
});
})();
*/


