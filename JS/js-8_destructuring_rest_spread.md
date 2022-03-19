
***
## Деструктуризация
***

#### Деструктуризация массивов

Начальный массив
  
`const arr = [2, 3, 4]` 
  
Для того, чтобы присвоить элементам массива переменные без деструктуризации
  
  `const a = arr[0]`
  `const b = arr[1]`
  `const c = arr[2]`
  
__Или через деструктуризацию__
  
  `const [a, b, c] = arr;`
  
  Чтобы пропустить объект в массиве в деструктуризированном присвоении нужно сделать пробел
```    
  const restaurant =
{
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
};

const [first,  , third] = restaurant.categories
```

__Чтобы поменять местами переменные__ 
```
[first, third] = [third, first]
```
Слева изначальные значения = справа те на которые они заменяются 

__Чтобы получать значения из массива через функцию через деструктуризацию__
```
const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  
  order: function (starterIndex, mainIndex)
  {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  }
};

restaurant.order(2, 0)  - получается название блюд из массивов starterMenu и mainMenu, которые
находятся под индексами 2 и 0.

чтобы записать их в отдельные переменные и сразу их создать через деструктуризацию

const [starter, main] = restaurant.order(2, 0) 
```

__Чтобы деструктуризовать вложенные массивы__ 
```
const nested = [0, 2, [5, 6]]

[a, b, [c, d]] = nested 
```

__Если длина масива неизвестна можно присваивать значения переменным через деструктуризацию,
которым они будут присвоены по умолчанию__
```
[a=1, b=1, c=1] = [4, 5]
```
В этом случае c будет равняться не undefined а 1

Пример деструктуризации массива
```
const animals = [
  { name: "cat",
  sound: "meow" },
  
  { name: "dog", 
  sound: "woof" }
];
const [cat, dog] = animals;
```

#### Деструктуризация объекта
```
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],

  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // Open 24 hours
      close: 24,
    },
  },
};
```
Нужно :
порядок присовения не имеет значения, но нужно точно использовать названия параметров 
`const {name, openingHours, categories} = restaurant;`

__Чтобы задать новое имя для переменной-параметра объекта, нужно указать ее чреез двоеточие__
```
const {name: RestaurantName, openingHours:restaurantOpeningHours, categories: RestaurantNameMenu} = restaurant;
```
__Для того, чтобы задать значение по умолчанию параметрам объекта и дать им также новые имена:__
создается переменная, в ней в скобках дается название параметра, через двоеточие если нужно - новое имя переменной, в  квадратных скобках значение по умолчанию
`const { starterMenu: starters = [defaultValue]} = restaurant;`
если в квадратных скобках не указано ничего, а у параметра есть значения в объекте, то они и используются по умолчанию.

__Мутация значений__
значения по умолчанию
```
let a = 111;
let b = 999;
```
переназначение переменных в объекте
`const obj = { a: 23, b: 7, c: 14 }`

мутация значений переменных через деструктуризацию
`({ a, b } = obj);`
без круглых скобок код работать не будет ! они нужны для того, чтобы движок js понимал, что это не блок кода, а деструктуризация

__Вложенные объекты (см. объект restaurant выше)__
вызывается параметр из нужного объекта, при указании этого объекта после двоеточия в скобках указываются параметры его как объекта
`const { fri: {open, close} }  = openingHours;`

__Для присвоения им имен они указываются через двоеточие__
`const { fri: {open: openHour, close: closeHour} }  = openingHours;`

__Для деструктуризации параметров функции__
(передается один аргумент, но 3мя параметрами объекта, которые сразу деструктуризируются. При этом порядок может быть произвольный.)
```
const restaurant = {
orderDelivery: function ({name, categories, location, })  
}

restaurant.orderDelivery =
{
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
}
```

__Можно дать названия элементам массива (или объекта)__

`const [red, green, blue] = [9, 33, 456];`
`console.log(green) будет 33.`

Пример деструктуризации объекта (после того, как он был выделен в массиве как переменная cat)
`+const {name, sound} = cat;`
name и sound экваивалентны cat.name и cat.sound

В объекте название переменных должно совпадать с названием деструктуризированных переменных.
Чтобы задать новые названия нужно указать их через двоеточие:
`+const {name: catName, sound: catSound} = cat;`

Для установления значения по умолчанию 
`const {name = "Tysya", sound = "Meow"} = cat;`

__Вложенные объекты:__

Исходный объект (переменная cat выделена в коде ранее):
```
const animals = [
  { name: "cat", sound: "meow",  feeding:
    {
    food: 2
    water: 3
    },
  {name: "dog", sound: "woof" }
];
```
Деструктуризированный:
```
const { name, sound, feeding: {food, water} } = cat;
console.log(food) === 2
console.log(water) === 3
```

#### Деструктуризация с функцией

Функция:
```
function useAnimals (animal) 
{
 return 
 [
  animal.name
  function ()
    {
    console.log(animal.sound)
    }
 ];
}
```
Деструктуризация:
```
const{animal, makeSound} = useAnimals(cat);
makeSound будет функцией с заданным параметром.
```

======= Челлендж Деструктуризация =======
\\ Файл с данными
```
const cars = [
  {
    model: "Honda Civic",
    coloursByPopularity: ["black", "silver"],
    speedStats: {
      topSpeed: 140,
      zeroToSixty: 8.5
    }
  },
  {
    model: "Tesla Model 3",
    coloursByPopularity: ["red", "white"],
    speedStats: {
      topSpeed: 150,
      zeroToSixty: 3.2
    }
  }
];
```
Код с выводом в таблицу
деструктуризация массива 1 уровня
`const [honda, tesla] = cars;`
деструктуризация и присвоение имени для пемеренной "скорость"
```
const {
  speedStats: { topSpeed: hondaTopSpeed }
} = honda;
const {
  speedStats: { topSpeed: teslaTopSpeed }
} = tesla;
```
деструктуризация и присвоение имени для пемеренной "цвет"
```
const {
  coloursByPopularity: [hondaTopColour]
} = honda;
const {
  coloursByPopularity: [teslaTopColour]
} = tesla;
  <table>
    <tr>
      <th>Brand</th>
      <th>Top Speed</th>
      <th>Top Colour</th>
    </tr>
    <tr>
      <td>{tesla.model}</td>
      <td>{teslaTopSpeed}</td>
      <td>{teslaTopColour}</td>
    </tr>
    <tr>
      <td>{honda.model}</td>
      <td>{hondaTopSpeed}</td>
      <td>{hondaTopColour}</td>
    </tr>
  </table>,
```
***
## Spread operator : позволяет объединять массивы, вписывая все значения массива отдельно как если бы по нему прошлись циклом.
***

Работает со всеми итерируемыми элементами, но не объектами.
(массивы, мэп, строки, set-объекты)

Берет все элементы массивы и в отличие от деструктуризации не создает новые переменные, а только "вписывает" в создавамый массив или когда передаем значение в функцию

Исходный массив
`const arr =  [7, 8, 9]`

Без спрэд-оператора сделать новый массив с цифрами 1 и 2 в начале и добавить все из массива arr 
`const badNewArr = [1, 2, arr[0], arr[1], arr[2] ]`

Со спрэд-оператором
`const newArr = [1, 2, ...arr]`

Без спрэд-оператора 
`[1, 2, arr]` массив arr был бы включен как массив а не отдельными значениями

если использовать массив newArr без спрэд-оператора, то в аутпут будет в виде массива
`console.log(newArr)`

если со спрэд-оператором то он будет как отдельные значения через пробел
`console.log(...newArr)`

Использование:
- копирование массива
`const copyArray = [...oldArray]`
- объединение массивов
`const mergeArray = [...firstArray, ... secondArray]`

__Передача значений в функцию через спрэд-оператор__
````
const orderPasta = function (ing1, ing2, ing3)
{
console.log(`This is a pasta with ${ing1}, ${ing2}, ${ing3})`
}
const ingridients = [a, b, c]
orderPasta(...ingridients)
```
C объектами спрэд-оператор работает так
Для добавления значений
```
const restaurant =
{
    menu: [pizza, salad],
    time: '06:00 - 00:00',
}
const new restaurant = {...restaurant, founder: ''Aaron,}
```

Для копирования объекта через спрэд-оператор.
Объект при этом копируется - то есть, создается новый.
`const restaurantCopy = {...restaurant}`

***
## Rest operator : обратный от spread, объединяет в массив значения
***

Практическое применение:
1) при деструктуризации
пример rest (слева от знака присвоения)
```
const [a, b,  ...others] = [1, 2, 3, 4, 5]
```
(значения 3, 4, 5 будут записаны в переменную others в виде массива)

Дан массив
`const array = [1, 2, 3, 4]`
чтобы присвоить первому значению (1) из массива переменную one
а остальные записать в другую переменную others 
`const [one, ...others] = array`

В объекте - создается новый.
```
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // Open 24 hours
      close: 24,
    },
  },
};

const {sat, ...weekdays } = restaurant.openingHours.
```
в переменную weekdays попадут fri и thu

2) передача значений в функцию
Чтобы передавать большое количество значений в функцию (нефиксированное) можно использовать этот оператор
"rest parameters"
```
const add = function (...numbers) 
{
    log///
}

add(4,5,6)
add(1,2,3,4,5)
add(3,5,6,7,3,2,1)
```
В каждом случае вызова функции параметры будут передаваться в виде массива с этими значениями  

Чтобы добавить массив как параметр функции 
```
const x = [23, 5, 7]
add (...x)
```
