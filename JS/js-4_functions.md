***
## Функции
***

ВАЖНО:
при переназначении внутри функции переменных они не меняют сами переменные вне функции. 
при мутации объектов или их значений внутри функций они изменяют сам объект

```
function getMilk()
{
    alert (get milk);
}
```
Вызов
```
getMilk();
```

___Параметры и аргументы функции___

```
function getMilk(money) \\ money - параметр
{
    alert ("Move right");
    alert ("Move straight");

    var numberOfBottles = Math.floor(money * 1.5);

    alert ("Get" + numberOfBottles + "milk");
    alert ("Get milk");
}

getMilk(12); \\ 12 - аргумент
```

***
#### Способы создания функции: DECLARATION \ EXPRESSION
***

 __[ ! ] Основное отличие между ними: функции, объявленные как Function Declaration, создаются интерпретатором до выполнения кода.__

__1. DECLARATION__ : не хранится в переменной, с названием функции. Можно вызвать до ее объявления
```
function calcAge(birthYear)
{
    return 2037 - birthYear
}   

// вызов
const age = calcAge (1986)
```

__2. EXPRESSION__ : хранится в переменной, без названия функции. Нельзя вызвать до ее объявления
```
const age = function (birthYear)
{
    return 2037 - birthYear
}

// вызов
const age = calcAge (1986)
```

***
Параметры по умолчанию (после равно)
***
```
const age = function (
birthYearA = 1999 или
birthYearB = 1999-234 или
birthYearC = birthYearB -234)
{
    return 2037 - birthYear
}
```

Чтобы пропустить один из параметров, который посередине и который уже имеет значение по умолчанию, но при вызове функции его не нужно прописывать - его при вызове функции можно ставить как undrfined   

```
const bookings = [];
const createBooking = function (
  flightNum,
  numPassengers = 1,
  price = 199 * numPassengers
) {
  // ES5
  // numPassengers = numPassengers || 1;
  // price = price || 199;

  const booking = {
    flightNum,
    numPassengers,
    price,
  };
  console.log(booking);
  bookings.push(booking);
};

createBooking('LH123');
createBooking('LH123', 2, 800);
createBooking('LH123', 2);
createBooking('LH123', 5);

createBooking('LH123', undefined, 1000);
```

***
#### Функции 1 класса и функции высшего порядка
***
__Функция 1 класса__ : имеется в виду концепция, при которой функции в JS могут быть переменными (они являются объектами) а значит - передаваться в другие функции или возвращаться из других функций.

__Функция высшего порядка__ : имеется в виду практическая реализация - функция, которая принимает в себя или использует в себе другие функции.

__Вызов функций__
__1. "Обычный" вызов__
Функция, которая будет вызываться внутри второй функции__
```
function cutFruitPieces(fruit)
{
    return fruit * 4
}
```
Функция, в которой вызывается 1 функция
```
function fruitProcessor(apples, oranges) 
{
    const  applePieces = cutFruitPieces(apples) 
    const  orangePieces = cutFruitPieces(oranges)
    
    const juice = `Juice with ${apples} apples and ${oranges} oranges.`
    return juice;
}
```

__2. Callback__
1) выполняется не сразу, а при вызове другой функции,
2) функция, использующая callback это функция высшего порядка

```
const oneWord = function (str)
{
  return str.replace(/ /g, '').toLowerCase();
};

const upperFirstWord = function (str)
{
  const [first, ...others] = str.split(' ');
  return [first.toUpperCase(), ...others].join(' ');
};

// Higher-order function *******(fn - функция - callback)*******
const transformer = function (str, fn)
{
  console.log(`Original string: ${str}`);
  console.log(`Transformed string: ${fn(str)}`);
  console.log(`Transformed by: ${fn.name}`);
};

transformer('JavaScript is the best!', upperFirstWord);
transformer('JavaScript is the best!', oneWord);
```


__3. Функция возвращает функцию__
```
const greet = function (greeting)
{
    return function (name)
    {
        console.log(`${greeting} ${name}`)
    }
}
```

Вызов:
Этап 1) `const greetingHey =  (`Hey`)` \\ добавляет при вызове в переменную greeting слово `Hey`
Этап 2) `greetingHey(`ALex`)` \\  Возвращает строку `Hey Alex`

Пример одновременного вызова
`greet (`Hello`)(`Alex`)` \\ Возвращает строку `Hello Alex`

***
// Immediately Invoked Function Expressions (IIFE)
***

функция, которая срабатывает однажды и далее никогда более 
ранее использовалась чтобы скрыть данные из области видимости, теперь в асинхронном программировании
Примеры:

__IIFE - обычная функция__
```
(function () {
  console.log('This will never run again');
  const isPrivate = 23;
})();
```

__IIFE - стрелочная функция__
(() => console.log('This will ALSO never run again'))();

***
### Стрелочные функции \ ARROW FUNCTIONS
***
Пример 1.
Вместо
```
function calcAge1(birthYear)
{
    return 2037 - birthYear
}
```
так (1 параметр и 1 строчка возврата)
```
birthYear => 2037 - birthYear
```

Пример 2.
```
const movementsUSD = movements.map(function(mov)
{
    return mov * eurToUsd
}
```

то же самое с arrow function
```
const movementsUSD = movements.map (mov => mov * eurToUsd)
```

> cохранение в переменной:
```
const calcAge = birthYear => 2037 - birthYear
```

> вызов (с сохрением в переменной):
```
const age = calcAge(1991)
```

> (один параметр и несколько строчек)
```
const yearUntilRetirement = birthYear => 
{
    const age = 2037 - birthYear
    const retirement = 65 - age
    return retirement
}
```
> (несколько параметров и несколько строчек)
```
const yearUntilRetirement = (birthYear,  firstName) =>
{
    const age = 2037 - birthYear
    const retirement = 65 - age
    return `${firstName} retires in ${retirement} years`
}
```
> функция, возвращающая функцию в виде стрелочной функции

Исходная 
```
const greet = function (greeting)
{
    return function (name)
    {
        console.log(`${greeting} ${name}`)
    }
}
```

Стрелочная
```
const greetArrow = greeting => name => console.log(`${greeting} ${name}`)
```

> Обычная и стрелочная функция (с тернарным оператором)
Обычная
```
const bill = 100
function calcTip1 (billValue)
{
    let billTip
     if (billValue >= 50 && billValue <= 300)
    {return billTip = billValue*15/100}
    else
    {return billTip = billValue*20/100}
}
```
Стрелочная
```
const calcTip2 = billValue => billValue >= 50 && billValue <= 300 ? billValue*15/100 : billValue*20/100

const tip1 = calcTip1(bill)
const tip2 = calcTip2(bill)
console.log(`The bill was ${bill}, the tip was ${tip1}, and the total value ${bill + tip1}`);
console.log(`The bill was ${bill}, the tip was ${tip2}, and the total value ${bill + tip2}`);
```

***
#### __Методы call(), bind(), apply()__ : Эти методы определяют что будет означать по умолчанию this
***

```
const lufthansa = {
  airline: 'Lufthansa',
  iataCode: 'LH',
  bookings: [],
  // book: function() {}
  book(flightNum, name) {
    console.log(
      `${name} booked a seat on ${this.airline} flight ${this.iataCode}${flightNum}`
    );
    this.bookings.push({ flight: `${this.iataCode}${flightNum}`, name });
  },
};
lufthansa.book(239, 'Jonas Schmedtmann');
lufthansa.book(635, 'John Smith');
const eurowings = {
  airline: 'Eurowings',
  iataCode: 'EW',
  bookings: [],
};
const book = lufthansa.book;
// Does NOT work
// book(23, 'Sarah Williams');
```

поскольку переменная book, в которую записана функция из объекта, не переносит окружение
из объекта, а создает свою соственную функцию, простой вызов не сработает, так как
потребуется привязка this к этой функции, а она теряется при сохранении в новой переменной. 

Для этого используются методы call \ apply \ binds.
Эти методы определяют что будет означать по умолчанию this

***
__ Call() __
***

`book.call(eurowings, 23, 'Sarah Williams');` \\ первая переменная означает откуда
"берется окружение", какой берется объект за основу, то есть применительно к чему 
будет браться this.
То есть, часть кода может использоваться из другого объекта, но работать он буддет
в том на который указан (в данном случае функция book идет из первого объекта lufthansa,
но результат ее выполнения записывается в объект eurowings).

!При этом названия значений объекта, в который записывается значение должно быть
одинаковым во всех объектах - из которого берется изначально код и в который записывается!

```
console.log(eurowings);

book.call(lufthansa, 239, 'Mary Cooper');
console.log(lufthansa);

const swiss = {
  airline: 'Swiss Air Lines',
  iataCode: 'LX',
  bookings: [],
};

book.call(swiss, 583, 'Mary Cooper');
```
***
__APPLY()__
***

Apply method - не берет лист аргументов из объекта как при вызове book
ранее book.call(swiss, 583, 'Mary Cooper'), а берет их из массива. 
Не применяется широко последнее время (заменяется методом call со spread оператором - см. ниже)
```
const flightData = [583, 'George Cooper'];
book.apply(swiss, flightData);
console.log(swiss);
```

В современном JS можно совмещать и заменить apply() методом call() использую spread оператор
Это 
`book.call(swiss, ...flightData);`
***
bind()
***
не вызывает функцию сразу, а возращает функцию, где this определено

```
\\ вместо вызова
book.call(eurowings, 23, 'Sarah Williams');
book.call(lufthansa, 23, 'Sarah Williams');
book.call(swiss, 23, 'Sarah Williams');

\\ функция записывается в переменную
const bookEW = book.bind(eurowings);
const bookLH = book.bind(lufthansa);
const bookLX = book.bind(swiss);

\\ вызывается
bookEW(23, 'Steven Williams');
bookLH(23, 'Steven Williams');
bookLX(23, 'Steven Williams');

\\ для задания одного или нескольких аргументов (лист аргументов) они 
указываются по порядку. К примеру, 23 рейс записан по умолчанию

const bookEW23 = book.bind(eurowings, 23);

\\ вызов
bookEW23('Jonas Schmedtmann');
bookEW23('Martha Cooper');

\\ Работа с  Listeners
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  console.log(this);

  this.planes++;
  console.log(this.planes);
};

document
.querySelector('.buy')
.addEventListener('click', lufthansa.buyPlane.bind(lufthansa)); \\ используется
bind метод для указания из какого объекта брать this

// Partial application - метод bind используется в первую очередь для установления
исходных значений, а не для определения this

const addTax = (rate, value) => value + value * rate;
console.log(addTax(0.1, 200));

const addVAT = addTax.bind(null, 0.23); \\ rate устанавливается в 0.23 всегда.
поскольку this в данном случае неважен, значение в обычной практике устанавливается как null
то же самое что и 
addVAT = value => value + value * 0.23;

console.log(addVAT(100));
console.log(addVAT(23));

// Использование функции, возвращающую функцию вместо кода выше

const addTaxRate = function (rate) {
  return function (value) {
    return value + value * rate;
  };
};
const addVAT2 = addTaxRate(0.23);
console.log(addVAT2(100));
console.log(addVAT2(23));
*/
```




