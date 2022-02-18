***
#### ООП
***
__Объектно-ориентированное программирование - парадигма (стиль написания кода, то есть как его пишут и организуют) основанная на концепции объектов__

1. Используются объекты для описания (моделирования) реальных или абстрактных явлений (html код и пр)
2. Объекты могут содержать информацию (свойства и код(методы). Используя объекты можно упаковать код в одном блоке
3. В ООП объекты самоупакованные части\блоки кода 
4. Объекты - блоки кода и взаимодействуют в приложениях друг с другом
5. Взаимодействие происходит через публичные интерфейсы (API) - внешние методы через которые снаружи объектов осуществляется взаимодействие с объектами и между ними  

__Классы - прототипы объектов.__
__Методы - устоявшееся обозначение свойств предметов, если ими выступают функции.__

__Принципы построения классов__
1. __Абстрактность__ - берется только то что нужно без ненужных деталей
2. __Инкапсуляция__ - означает, что некоторые методы и параметры содержатся внутри класса и недоступны извне в связи с тем, что они важны только для работы этого класса. Внешнее воздействие при этом может навредить. Некоторые способы обеспечить безопасность кода - внизу.
3. __Наследование__ - есть родительские классы и есть наследованные классы, расширяющие родительский, благодаря чему не будет лишнего дублирования кода
4. __Полиморфизм__ - дочерние элементы могут переписывать методы, наследованные от родителей

Класс позволяет на его основе делать экземпляр объекта.

[ ! ] Объекты\экземпляры, связанные с прототипом, могут использовать методы прототипа (прототипное наследование)
Таким образом, объекты делегируют прототипу свое поведение

Метод обнаружения родительского элемента
объект `instanceof` прототип \\ true-false

#### __Способы создания прототипов__
##### 1. Функция - конструктор -- создание объекта через функцию, изначальный метод (по нему созданы массивы и пр.)
```
// Constructor Functions and the new Operator
const Person = function (firstName, birthYear) {
  // Instance properties
  this.firstName = firstName;
  this.birthYear = birthYear;
  // Не добавлять методы в конструктор таким образом - так как создается каждый раз копия функции!
  // this.calcAge = function () {
  //   console.log(2037 - this.birthYear);
  // };
};

// метод добавляется извне следующим образом
Person.prototype.calkAge = function()
{
    log(2037 - this.birthYear)
}

// person.prototype это не прототип конструктора person, а прототип для всех объектов, которые созданы через конструктор Person. То есть это прототипы связанных с конструктором объектов 

const jonas = new Person('Jonas', 1991);
console.log(jonas);
```

Что происходит при вызове оператора new
1. Создается новый пустой объект
2. Ффункция вызывается, this становится этим объектом = {}
3. Объект устанавливает связь с прототипом
4. Функция автоматически возвращает объект {}

```
const matilda = new Person('Matilda', 2017);
const jack = new Person('Jack', 1975);
console.log(jonas instanceof Person);

console.log(Person.prototype);
Person.prototype.calcAge = function () {
  console.log(2037 - this.birthYear);
};

jonas.calcAge();
matilda.calcAge();

console.log(jonas.__proto__);
console.log(jonas.__proto__ === Person.prototype);

console.log(Person.prototype.isPrototypeOf(jonas));
console.log(Person.prototype.isPrototypeOf(matilda));
console.log(Person.prototype.isPrototypeOf(Person));

// .prototyeOfLinkedObjects

Person.prototype.species = 'Homo Sapiens';
console.log(jonas.species, matilda.species);

console.log(jonas.hasOwnProperty('firstName'));
console.log(jonas.hasOwnProperty('species'));

///////////////////////////////////////
// Prototypal Inheritance on Built-In Objects
console.log(jonas.__proto__);
// Object.prototype (top of prototype chain)
console.log(jonas.__proto__.__proto__);
console.log(jonas.__proto__.__proto__.__proto__);
```

__Методы__
__species()__ : добавление параметров к прототипу.
Значение не будет в самом объекте, а будет наследоваться им из прототипа (общего)
Person.prototype.species = 'Human'
log(jonas.species) \\\ 'Human'

__hasOwnProperty()__ : проверить, есть ли параметр в объекте 
log(jonas.hasOwnProperty'firstName')

##### 2. ES6 классы : улучшенный синтаксис конструкторов, один уровень абстракции над ними, но по сути это тот же конструктор

Методы создания:
__Class expression__
`const PersonCl = class {}`
__Class declaration__
`class PersonCl {`
  `constructor(fullName, birthYear) {`
   ` this.fullName = fullName;`
   ` this.birthYear = birthYear;`
 `}`

Примеры методов:

> Методы будут добавлены к .prototype property
  calcAge() {
    console.log(2037 - this.birthYear);
  }
  greet() {
    console.log(`Hey ${this.fullName}`);
  }
  get age() {
    return 2037 - this.birthYear;
  }

  > Установить свойство, которое уже существует
  set fullName(name) {
    if (name.includes(' ')) this._fullName = name;
    else alert(`${name} is not a full name!`);
  }
  get fullName() {
    return this._fullName;
  }

Особенности классов:
1. Классы не "поднимаются". Даже при класс-декларации он не будет доступен до того как декларирован
2. Классы - первого порядка (могут быть использованы в других функциях и возвращаться из них)
3. Классы извлекаются движком даже если соответствующие функции не была вызвана (strict mode)

##### 3/ Obect.create() : самый простой метод создания, минуя конструктор.
На практике используется после 1 и 2.
Также используется для наследования между классами (прототипами)
```
const PersonProto = {
  calcAge() {
    console.log(2037 - this.birthYear);
  },

  init(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  },
};

const steven = Object.create(PersonProto);
console.log(steven);
steven.name = 'Steven';
steven.birthYear = 2002;
steven.calcAge();

console.log(steven.__proto__ === PersonProto);

const sarah = Object.create(PersonProto);
sarah.init('Sarah', 1979);
sarah.calcAge();
```


__Статические методы__ : методы, которые связаны с конструктором, а не с копиями экземпляров (то есть прототипом)

=======
getters\setters - функции, доступные объектам, которые получают или вводят данные в объект. это параметры объекта, а не методы.
Позволяют реализовать логику.  

«get» – для чтения \ «set» – для записи
=======

Пример 1:
```
const account = {
  owner: 'Jonas',
  movements: [200, 530, 120, 300],

  get latest() {
    return this.movements.slice(-1).pop();
  },

  set latest(mov) {
    this.movements.push(mov);
  },
};
console.log(account.latest);
account.latest = 50;
console.log(account.movements);
```

Пример 2: 
```
let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  }
};

alert(user.fullName); // John Smith
```

***
##### Наследование классов \ прототипов 
***

__1. У конструкторов через Object.create()__
```
const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
};
Person.prototype.calcAge = function () {
  console.log(2037 - this.birthYear);
};
const Student = function (firstName, birthYear, course) {
  Person.call(this, firstName, birthYear);
  this.course = course;
};
```

> создание ссылки - между прототипо Student и прототипом Person.
Код помещается до добавления методов прототипу иначе он перезапишет методами прототип

```
Student.prototype = Object.create(Person.prototype);
Student.prototype.introduce = function () {
  console.log(`My name is ${this.firstName} and I study ${this.course}`);
};
const mike = new Student('Mike', 2020, 'Computer Science');
mike.introduce();
mike.calcAge();
console.log(mike.__proto__);
console.log(mike.__proto__.__proto__);
console.log(mike instanceof Student);
console.log(mike instanceof Person);
console.log(mike instanceof Object);
```

> поскольку прототип сделан через object.create, при логгировании прототип student указывает не то что на конструктор student это student, а на Person. чтобы это уточнить можно использовать следующий код 

```
Student.prototype.constructor = Student;
console.dir(Student.prototype.constructor);
*/
```

__2. У классов__
```
class PersonCl {
  constructor(fullName, birthYear) {
    this.fullName = fullName;
    this.birthYear = birthYear;
  }
  // Instance methods
  calcAge() {
    console.log(2037 - this.birthYear);
  }
  greet() {
    console.log(`Hey ${this.fullName}`);
  }
  get age() {
    return 2037 - this.birthYear;
  }
  set fullName(name) {
    if (name.includes(' ')) this._fullName = name;
    else alert(`${name} is not a full name!`);
  }
  get fullName() {
    return this._fullName;
  }

class StudentCl extends PersonCl {
  constructor(fullName, birthYear, course) {
    // Always needs to happen first!
    super(fullName, birthYear);
    this.course = course;
  }

  introduce() {
    console.log(`My name is ${this.fullName} and I study ${this.course}`);
  }

  calcAge() {
    console.log(
      `I'm ${
        2037 - this.birthYear
      } years old, but as a student I feel more like ${
        2037 - this.birthYear + 10
      }`
    );
  }
}

const martha = new StudentCl('Martha Jones', 2012, 'Computer Science');
martha.introduce();
martha.calcAge();
```

__3. Между object.create()__
```
const PersonProto = {
  calcAge() {
    console.log(2037 - this.birthYear);
  },

  init(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  },
};

const steven = Object.create(PersonProto);

const StudentProto = Object.create(PersonProto);
StudentProto.init = function (firstName, birthYear, course) {
  PersonProto.init.call(this, firstName, birthYear);
  this.course = course;
};

StudentProto.introduce = function () {
  console.log(`My name is ${this.fullName} and I study ${this.course}`);
};

const jay = Object.create(StudentProto);
jay.init('Jay', 2010, 'Compuetr Science');
jay.introduce();
jay.calcAge();
```

***
__Инкапсуляция: Защищенные свойства и методы. Приватные поля классов и методы__
***
Нужно проверять доступность браузеров перед использованием.

// 1) Public fields
// 2) Private fields
// 3) Public methods
// 4) Private methods
// (there is also the static version)

```
class Account {
  // 1) Public fields (instances)
  locale = navigator.language;
```
```
  // 2) Private fields (instances)
  #movements = [];
  #pin;

  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.#pin = pin;

    // Protected property
    // this._movements = [];
    // this.locale = navigator.language;

    console.log(`Thanks for opening an account, ${owner}`);
  }
```
```
  // 3) Public methods

  // Public interface
  getMovements() {
    return this.#movements;
  }

  deposit(val) {
    this.#movements.push(val);
    return this;
  }

  withdraw(val) {
    this.deposit(-val);
    return this;
  }

  requestLoan(val) {
    // if (this.#approveLoan(val)) {
    if (this._approveLoan(val)) {
      this.deposit(val);
      console.log(`Loan approved`);
      return this;
    }
  }

  static helper() {
    console.log('Helper');
  }
```
```
  // 4) Private methods
  // #approveLoan(val) {
  _approveLoan(val) {
    return true;
  }
}

const acc1 = new Account('Jonas', 'EUR', 1111);

// acc1._movements.push(250);
// acc1._movements.push(-140);
// acc1.approveLoan(1000);

acc1.deposit(250);
acc1.withdraw(140);
acc1.requestLoan(1000);
console.log(acc1.getMovements());
console.log(acc1);
Account.helper();

// console.log(acc1.#movements);
// console.log(acc1.#pin);
// console.log(acc1.#approveLoan(100));

// Chaining
acc1.deposit(300).deposit(500).withdraw(35).requestLoan(25000).withdraw(4000);
console.log(acc1.getMovements());
*/
```

***
## OBJECTS \ ОБЪЕКТЫ
***
позволяет  использовать ключи - наименования\значения (property=свойства)

ПРИМЕР
```
const jonas =
{
    firstName: 'jonas',
    lastName: 'Schmedtmann',
    age: 342-123,
    job: 'teacher'
    friends: ['friend1', 'friend2', 'friend3']
    hasDriverLicense: true, 
    calcAge:  function (birthYear) 
    {
            return 2037-birthYear
    }
```
или
```
    calcAge:  function () 
    {
            return 2037-this.birthYear
    }
    // то же самое что и код ниже, но в этом случае при изменении названия объекта не потребуется менять код внутри
    calcAge:  function () 
    {
            return 2037-jonas.birthYear
    }
    // также можно записывать результаты функции-параметра объекта в новый параметр объекта
    calcAge:  function () 
    {
            this.age = 2037-this.birthYear
            return this.age
    }
}
```

__Обратиться к значению объекта__:
1. Через точку
`jonas.lastName`

2. Через квадратные скобки 
`jonas['lastName']`
// в этом случае значение может рассчитываться - может применяться любое expression 

__Добавление значения в объект__
`jonas.location = 'London'`
`jonas.['car'] = 'volga'`

__Вызов функции (метода) из объекта__
`jonas.calcAge(1991)`
или
`jonas.['calcAge'](1991)`

__THIS__ - метод, который равняется объекту, из которого вызывается метод или равняется объекту, вызывающего метод

__Работа движка JS__

  При изменении примитивных данных для нового значения в памяти stack выделяется новая ячейка с того момента когда до него дошла очередь исполнения. 
  
  При изменении сложных типов данных (объекты), меняется объект в heap через названия переменных (ссылка на объект в стэке в памяти), которые являются ключами к памяти в heap. Новая ячейка памяти в стеке не выделяется, новый объект в heap не создается, перезаписывается изначальный объект.
  Каждый объект внутри объекта является отдельным. 
  
 Для копирования объекта (merge) используется функция Object.assign, где аргументами являются имеющиеся объекты или новый пустой объект (чтобы просто скопировать, а не производить слияние)
 ПРИМЕР
  `(const objectNewCopy = Object.assign({}, objectOld)`
 
 Этот метод работает только на 1 уровне объектов.
 Для deep clone требуется отдельный метод.

__Литералы__
1. Улучшенный синтаксис литералов
основной
const newObject =
{example: 123};

2. До ES6 чтобы включить в объект как его значение другой объект нужно было (на примере объект openingHours включается в объект restaurant). Это может запутать если названия одинаковые. В ES6 можно просто сделать название - см. в примере
```
const openingHours =
{sun-sat: '12-23'};
const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  // до ES6
  openingHours: openingHours,
  // после ES6
  openingHours,
};
```
3. Добавление функции в объект
```
const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  // до ES6
  moveSuitcase: function (one, two) 
  {
        alert("May I take your suitcase?");
        pickUpSuitcase();
        movie();
  }
  // после ES6
   moveSuitcase (one, two) 
  {
        alert("May I take your suitcase?");
        pickUpSuitcase();
        movie();
  }
};
```
3. Можно рассчитывать названия переменных, а не указывать их литерально
чтобы включить значение в объект из массива (к примеру, дни недели) 
const weekdays = ['sun', 'mon', 'thu', 'fri']; 
```
const openingHours =
{[weekdays[1]]: '12-23',
[weekdays[2]]: '12-23',
[weekdays[3]]: '12-23'
}; 
```
или так
```
const openingHours =
{[`example day-${1+4}`]: '12-23',
}; 
```
__Опциональная цепочка__
Когда при указании значений объектов неизвестно точно что у этого объекта есть это значение.
К примеру, restaurant.openingHours.sat из когда ниже
неизвестно, будет ли у всякого объекта restaurant значение openingHours.sat.open
```
const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
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
Для этого нужно проверить, действительно ли значение имеет место когда будет запрошено
__без ES2020__
```
if (restaurant.openingHours.sat.open)
{
    restaurant.openingHours.sat.open
}
```
__после ES2020__ - опциональная цепочка (?.)
`restaurant.openingHours.sat?.open`
только если sat доступен open будет выполняться
если sat undefined или null результат будет сразу undefined или null, а не ошибка если бы вызов был без этого оператора.
Можно использовать много операторов сразу
`restaurant.openingHours?.sat?.open`
     
ПРИМЕР:
```
const days = ['sun', 'mon', 'thu', 'fri']; 

for (const day of days)
{
// квадратные скобки для day нужны так как это имя переменной. || ''closed - устанавливает значение по умолчанию - если open не определен то будет написано что закрыто

    const open = restaurant.restaurantOpeningHours[day]?.open || ''closed
    log (`On ${day} we open at ${open}`)
}
 ```
 но если значение будет 0 то такой код не сработает.
 Для этого нужен "нулевой" оператор
 вместо
   `const open = restaurant.restaurantOpeningHours[day]?.open || ''closed`
это
   `const open = restaurant.restaurantOpeningHours[day]?.open ?? ''closed`

Опциональная цепочка работает и с методами
К примеру, (order это функция)

`restaurant.order?.(0.1) ?? 'Метод недоступен'`

Работает также с массивами
`const users = [{name: 'My name', email: 'myemail@mail.io'}]`
`users[0]?.name ?? 'Массив пустой'`

***
#### Цикл в объектах
***
Нужно выбрать через что будет цикл.
Имена параметров, их значения или оба из них (обобщенное называется keys).
Испоьзуется цикл for of, также через массив, но в него будет добавлен нужный объект

1. Для прохождения цикла по названиям свойств 

//исходный объект
```
const restaurant =
{
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
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

`const properties = Object.keys(restaurant.openingHours)`
// переменная properties будет состоять из массива со свойствами объекта. 

// чтобы по ним пройтись циклом (вместо Object.keys(openingHours) тут можно использовать properties
```
for (const day of Object.keys(restaurant.openingHours))
{ 
log(day)
}
```

// также можно улучшить этот код
```
const properties = Object.keys(restaurant.openingHours)
let openStr = `Мы открыты ${properties.lenght} дней: `
for (const day of properties)
{ 
    openStr += `$day, `
}
```

получится, что в переменной openStr после двоеточия будут добавляться названия свойств поочереди, причем это будет одна строка.  

2. Цикл по значениям свойств (values)
`const values = Object.values(openingHours)`
// в остальном также как в предыдущем случае

3. Чтобы получить и свойство и значение свойства нужно использовать метод entries. Он возвращает индек значения и само значение.
```
const entries = Object.entries(openingHours)
for (const x of entries)
{
    log(x) - пройдет циклом и выведет все свойства и их значения
}
```
чтобы использовать это на практике можно использовать вместо x деструктуризацию. Поскольку объект сложный придется использовать {}.
В более простом случае можно было бы писать использовать такой синтаксис [day, values]
```
for (const [day, {open, close}] of entries)
{   
    log(`On ${day} we open at ${open} and close at ${close}`)
}
```
другой пример
```
for (const [goalNumber, goalPlayer] of game.scored.entries())
{
    console.log(`Goal ${goalNumber + 1}: ${goalPlayer}`);
}
```
замечание
`game.scored.entries()` - используется для массива
`Object.entries()`- используется для объекта

***
#### Создание Объекта JS
***

Пример:
```
var houseKeeper1 = 
{
    yearsOfExperience: 12;
    name: "Jane";
    cleaning: ["bathroom", "lobby", "bathroom"]
}
```
Функция - конструктор объектов. Первая буква названия обязательно заглавная.
```
function BellBoy (name, age, hasWorkPermit, languages)
{
    this.name = name;
    this.age = age;
    this.hasWorkPermit = hasWorkPermit;
    this.languages = languages;
}
```
Инициализация:
```
var bellBoy1 = new BellBoy("Timmy", 19, true, ["French", "English"]);
```
