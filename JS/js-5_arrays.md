***
## ARRAYS \ Массивы
***
***
#### 2 способа создания
***
1. const ages = [1234, 1222, 4245]

2. const ages = new Array(1234, 1222, 4245)

> В массив можно включать рассчитываемые значения, в том числе вызов функции - все что являются expression
`const ages = [15*6, 674637+4664, 5657-6464]`
и
`const years = [1099, 1094, 2002, 2018]`
```
const calcAge = function (birthYear)
{
    return 2077 - birthYear
}
const ages = [calcAge(years[0]), calcAge(years[1]) ]
```

> В массив можно включать определенные извне переменные
`const age1 = 456`
`const ages = [age1, 545+4664, 5657-6464]`

> В массив можно включать другие массивы 

> В массив можно включать разные типы данных

> В массиве нельзя делать расчеты с использованием самого массива, только к его элементам

***
#### __Методы массивов__
***

__push()__ : добавляет элемент в конец массива   
`названиеМассива.push('название элемента\строка')`

__unshift()__ : добавляет элемент в начало массива
`названиеМассива.unshift('название элемента\строка')`

__pop()__ : убирает последний элемент
`названиеМассива.pop('название элемента\строка')`

__shift()__ : убирает первый элемент
`названиеМассива.shift('название элемента\строка')`

__indexOf()__ : возвращает номер элемента в массиве
`названиеМассива.indexOf('название элемента\строка')`

__includes()__ : возвращает true\false если элемент в массиве или не в массиве. Использует строгое соответствие
`названиеМассива.includes('название элемента\строка')`

__slice()__ : вырезает часть массива без изменения массива, создает новый.
`arr.slice (стартовая позиция)`
`arr.slice(2)` \\ со второго индекса до конца
`arr.slice(2, 4)` \\ со второго до четвертого не включая четвертый
`arr.slice(-2)` \\ два последних
`arr.slice(-1)` \\ последний элемент
`arr.slice(1, -2)` \\ c первого до двух последних
`arr.slice()` \\ полная копия массива - аналог spread [...arr]

__splice()__ : аналог slice, но он мутирует изначальный массив - убирая из него вырезанные элементы.
Использование такое же как slice.
На практике используется для удаления элементов из массива.
При этом различие в методе удаления.
`arr.splice(1, 2)` \\ вырезает и оставляет начиная с 1 = первого 2 = два элемента (количество элементов для удаления).

__reverse()__ : меняет (переворачивает) порядок элементов в массиве. Мутирует оригинальный массив.

__concat()__ : объединяет массивы, не мутирует оригинальный массив
`const letters = array1.concat(array2)`
Альтернатива через деструктуризацию
`[...array1, ...array2]`

__join()__ : создает строку, элементы которой разделены заданным символом
`array.join( ' + ')`

***
__Создание массивов программно__
***

Через конструктор
`const x = new Array(7)` \\\ создает пустой массив с 7 элементами

Наполнение 
\\ метод fill() (мутирует массив)
`fill(1)` - заполняет массив значением 1
`fill(1, 3)` - заполняет массив значением 1 с третьего индекса
`fill(1, 3, 5)` - заполняет массив значением 1 с третьего по пятый индекс 

\\Array.from() - метод, применяемый к объекту Array.
`Array.from({length: 7},  () => 1)` \\ создает массив длиной 7 и заполняет его как
если бы применялся метод map цифрой 7

`Array.from({length: 7},  (currentElement, i) => i + 1 )` \\ создает  массив длиной 7
и заполняет его цифрами индекс + 1 на каждой итерации

_Главное практическое использование - создание массива из массивоподобных элементов_
Еще один способ - добавить необходимый элемент через спрэд оператор в новый массив

***
#### LOOPS ЦИКЛ
***
__1.FOR__ - работает до тех пор, пока условие не станет false. запустится минимум 1 раз

// Вместо
```
console.log('1')
console.log('2')
console.log('3')
console.log('4')
console.log('5')
console.log('6')
```
// цикл
```
for (let rep = 1; rep <=6; rep++)  
{
    console.log(rep)
}
```

// цикл FOR для перебора массивов 
```
const jonas =
[
     'Jonas',
     'Schmedtmann',
     342-123,
     'teacher',
     ['friend1', 'friend2', 'friend3']
]

for (i=0; i<=5; i++)
{
    console.log(jonas[i], typeof jonas[i] )
}
```
//или
```
for (i=0; i<=jonas.length; i++)
{
    console.log(jonas[i] typeof jonas[i])
}
```

// ПРИМЕР добавление значений из одного массива в другой через цикл
```
const type = []
for (i=0; i<=jonas.length; i++)
{
    // ПРИМЕР чтение массива
    console.log(jonas[i] typeof jonas[i])

    // ПРИМЕР наполнение массива оператором присвоения
    types [i] = typeof jonas [i]

    // ПРИМЕР наполнение массива методом push
    types.push(typeof jonas[i])
}
```
// ПРИМЕР сложение значений в массиве и сохранение их в новый массив
```
const years = [1991, 2059, 2077, 1969]
const ages = []

for (let i = 0; i <= years.length; i++)
{
    ages.push(3000 - years[i])
}
```
// CONTINUE STATEMENT - выходит из текущей итерации и продолжает следующую в рамках цикла
 в примере в консоль выводятся только те значения массива, которые ЯВЛЯЮТСЯ строками 
```
for (i=0; i<=jonas.length; i++)
{
    if (typeof jonas[i] !== 'string') continue
   
   console.log (jonas[i])
}
 ```
 
// BREAK STATEMENT - прекращает цикл
в примере ниже цикл прекращается при нахождении типа данных - число
```
for (i=0; i<=jonas.length; i++)
{
    if (typeof jonas[i] === 'number') break
}
```

// ПРИМЕР - обратный цикл
```
for (let i = jonas.length - 1; i >= 0; i--)
{
    console.log(jonas[i]);
}
```
// ПРИМЕР - цикл внутри цикла. Выведет 3 лога по 5 логов внутри каждого.  
```
for (let exercise = 1; exercise >= 3; exercise++)
{
    console.log(`------- Starting exercise ${exercise}`);

    for (let repitition = 1; repitition <6; repitition++
    {
        console.log(`------- Lifting weight ${repitition}`);
    }
}
```

переменная exercise доступна во втором цикле

__2. WHILE__ - требует условие, но не счетчик. Работает до тех пор, пока условие не
будет false. То есть, может работать без счетчика, отслеживая состояние. Цикл не будет
запущен никогда если условие изначально false.

// ВМЕСТО такого цикла
```
for (let rep = 1; rep <=6; rep++)  
{
    console.log(rep)
}
```
// ТАКОЙ
```
let rep = 1;
while (rep <= 10)
{
    console.log(rep)
    rep++
}
```

// ПРИМЕР использования цикла без счетчика. Задача - до тех пор, пока кубик не
выбросит цифру 6 кидать кубик
```
let dice = Math.trunc(Math.random() * 6) + 1
while (dice !== 6) 
{   
    console.log(dice)
    let dice = Math.trunc(Math.random() * 6) + 1 // создается новая переменная для того,
    чтобы не было бесконечного цикла так как в противном случае будет перезаписываться первая переменная
}
```

__3. FOR - OF__ - для перебора массивов

дан объект
```
const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
};
```

сделан массив
```
const menu = [...restaurant.starterMenu, ... restaurant.mainMenu] 
```

применяя for - of loop

`for (const item of menu)` \\ при выведении в консоль item покажет отдельно
каждый элемент массива menu
Можно использовать break и continue. Но проблема с индексами элементов. 
Чтобы получать индекс элементов
```
for (const item of menu.entries())
{
    в логе каждый item теперь будет содержит индекс как первый элемент массива
    и значение как второй
    
    чтобы вывести "красиво" рзультаты:
    
    log(`${item}[0] + 1: ${item[1]}`) 
}

или можно деструктуризовать их прямо при объявлении

for (const [index, element] of menu.entries())
{
    
}
```

__4. forEach__ для прохождения массива
(!) нельзя прервать как for of.
Не создает новый массив.
```
const movements = [100, 300, 485, -309, -453, -3444, 4555]
 \\--- пример с for of

for (const movement of movements)
{
    if(movement>0)
    {
        console.log(`You deposited ${movement})`)
    }
    else
    {
        console.log(`You withdrew ${Math.abs(movement)})`)
    }
 }
 
 \\--- пример с forEach
 
movement.forEach(function(movement)
{
    if(movement>0)
    {
        console.log(`You deposited ${movement})`)
    }
    else
    {
        console.log(`You withdrew ${Math.abs(movement)})`)
    }
 }

\\--- пример с for of вместе со счетчиком
  
for (const [i, movement] of movements.entries())
{
    if(movement>0)
    {
        console.log(`Movement ${i+1}: You deposited ${movement})`)
    }
    else
    {
        console.log(`Movement ${i+1}: You withdrew ${Math.abs(movement)})`)
    }
}

\\--- пример с forEach вместе со счетчиком

movement.forEach(function(movement, index, array)
{
    if(movement>0)
    {
        console.log(`Movement ${index+1}: You deposited ${movement})`)
    }
    else
    {
        console.log(`Movement ${index+1}: You withdrew ${Math.abs(movement)})`)
    }
 }

 \\\--- forEach для maps
 
const currencies = new Map
([
    ['USD', 'United States dollar'],
    ['EUR', 'Euro'],
    ['GBR', 'Pond sterling'],
])

currencies.forEach(function(value, key, map)
{
    console.log(`${key}: ${value})
}
 
\\\--- forEach для sets
 
const currenciesUnique = new Set 
([
    [USD],
    [GBR],
    [USD],
    [EUR],
    [EUR],
    [GBR],
])
  
currenciesUnique.forEach (function (value, value, map)
{
    console.log(`${value}: ${value}) \\ key имеет такое же значение как и value, так как это set
}
```
***
#### Сортировка массивов
***
Строки
__sort()__ - сортирует массив по начальным буквам алфавита. (!) Мутирует оригинальный массив. 

Чтобы сортировать массив состоящий из чисел от меньшего к большему или наоборот,
состоящий в том числе из отрицательных значений от меньшего к большему
```
array.sort((a, b) => 
{
    if (a > b) return 1
    if (b > a) return -1
})
```
или
```
array.sort((a, b) => a - b))
```
От большему к меньшему
```
array.sort((a, b) => 
{
    if (b > a) return -1
    if (a > b) return 1
})
```
или
```
array.sort((a, b) => b - a))
```
***
#### Использование методов в цепочке
***
// ПРИМЕР
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460],
const eurToUsd = 1.1
const totalDepositsUSD = movements.filter(mov => mov > 0).map(mov => mov * eurToUsd)
.reduce((acc, mov) => acc + mov, 0)
```
//мы можем добавлять эти методы только к тем, которые до них возвращали массив.
в данном случае reduce не возвращает массив, а значение

***
#### Перебор массива
***
__filter()__ : создание нового массива, если каждый элемент возвращает true.

Исходные данные
`var numbers = [3, 56, 2, 48, 5];`
чтобы отсортировать данные и вернуть только те что меньше 10: 
```
const newNumbers = numbers.filter(function(num)
{
return num < 10;
}
```
пример 2
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460],

const deposite = movements.filter(function (mov)
{
    return mov > 0
})
```
То же с for of
```
const depositsForOf = []
for (const mov of movements) if (mov > 0) depositsForOf.push(mov)
```

__reduce()__ : аккумулирует данные, делая что-то с каждым из них

Исходные данные
`var numbers = [3, 56, 2, 48, 5];`

чтобы взять одно число и затем, пройтись по массиву, прибавить или сделать
иные действия к этому числу другие действия - 
```
var newNumber = numbers.reduce(function(accumulator, currentNumber)
{
 return accumulator + currentNumber;
});
```
в данном случае accumulator имеет  значение первого числа 3, currentNumber второго
- 56, они складываются. на следующей итерации - повторятеся только первое число
-  становится суммой первых двух.

пример 2 (первый элемент прибавляет второй, к этому значению прибавляется третий и т.д.)
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460],
const balance = movements.reduce(function (accumulator, currentValue, index, array) 
{
    return accumulator+currentValue
}, 0 ) \\ стартовое значение accumulator
```
используя arrow 
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460]
const balance = movements.reduce((accumulator, currentValue, index, array) =>
accumulator+currentValue, 0 ) 
```
то же с for of
```
let balanceForOf = 0;
for (const mov of movements) balanceForOf += mov
```
нахождение масимального числа в массиве
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460]
const max = movements.reduce((acc, mov) => 
{
    if (acc > mov) return acc 
    else return mov
}, movements[0])
```

__find()__ : нахождение первого значения true (ищет первое совпадение в массиве и выводит его)

Исходные данные
```
var numbers = [3, 56, 2, 48, 5];
const number = numbers.find(function (num)
{
    return num > 10; 
});
```

Выведет 56 так как оно первое больше 10

стрелочный вид
```
var numbers = [3, 56, 2, 48, 5];
const numberBiggerThan0 = numbers.find(num => num < 0)
```
Отличия от filter
1) возвращает, первое значение, а не все
2) возвращает значение, а не массив

Пример поиска объекта в массиве, содержащем разные объекты - по содержанию параметра объекта
```
const account1 = {
  owner: 'Jonas Schmedtmann',
  movements: [200, 450, -400, 3000, -650, -130, 70, 1300],
  interestRate: 1.2, // %
  pin: 1111,
};

const account2 = {
  owner: 'Jessica Davis',
  movements: [5000, 3400, -150, -790, -3210, -1000, 8500, -30],
  interestRate: 1.5,
  pin: 2222,
};

const accounts = [account1, account2];

const account = account.find(acc => acc.owner === 'Jessica Davis')
```

__findIndex()__ - возвращает индекс первого элемента, который соответствует условию.
Работает как find Похож на метод indexOf, но в indexOf можно получать только булевое
значение (содержится ли это значение в массиве или нет)

__SOME()__ метод, проверяющий состояние массива. возвращает булевое значение -
"содержит ли нечто массив".
Отличие от includes() то что includes() проверяет на точное соответствие одного
конкретного значения массива, а some позволяет создавать проверочные условия.
```
const numbers = [3, 56, 2, 48, 5, -5, -38];
const anyDeposits = numbers.some(num => num > 0)
```
__every()__ метод, похожий на some() и проверяющий состояние массива. возвращает
булевое значение - "содержат ли все элементы массива нечто".
__flat()__
создает из массива с вложенными массивами единый массив. работает с одим уровнем вложенности по умолчанию.
```
const array = [[1,2] 3,4]
array.flat() \\ 1 уровень вложенности
array.flat(2) \\ 2 уровня вложенности
```
__flatMap()__
метод, соединяющий map + flat в одном. работает только на 1 уровне вложенности

