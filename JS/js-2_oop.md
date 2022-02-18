***
#### ���
***
__��������-��������������� ���������������� - ��������� (����� ��������� ����, �� ���� ��� ��� ����� � ����������) ���������� �� ��������� ��������__

1. ������������ ������� ��� �������� (�������������) �������� ��� ����������� ������� (html ��� � ��)
2. ������� ����� ��������� ���������� (�������� � ���(������). ��������� ������� ����� ��������� ��� � ����� �����
3. � ��� ������� ��������������� �����\����� ���� 
4. ������� - ����� ���� � ��������������� � ����������� ���� � ������
5. �������������� ���������� ����� ��������� ���������� (API) - ������� ������ ����� ������� ������� �������� �������������� �������������� � ��������� � ����� ����  

__������ - ��������� ��������.__
__������ - ����������� ����������� ������� ���������, ���� ��� ��������� �������.__

__�������� ���������� �������__
1. __�������������__ - ������� ������ �� ��� ����� ��� �������� �������
2. __������������__ - ��������, ��� ��������� ������ � ��������� ���������� ������ ������ � ���������� ����� � ����� � ���, ��� ��� ����� ������ ��� ������ ����� ������. ������� ����������� ��� ���� ����� ���������. ��������� ������� ���������� ������������ ���� - �����.
3. __������������__ - ���� ������������ ������ � ���� ������������� ������, ����������� ������������, ��������� ���� �� ����� ������� ������������ ����
4. __�����������__ - �������� �������� ����� ������������ ������, ������������� �� ���������

����� ��������� �� ��� ������ ������ ��������� �������.

[ ! ] �������\����������, ��������� � ����������, ����� ������������ ������ ��������� (����������� ������������)
����� �������, ������� ���������� ��������� ���� ���������

����� ����������� ������������� ��������
������ `instanceof` �������� \\ true-false

#### __������� �������� ����������__
##### 1. ������� - ����������� -- �������� ������� ����� �������, ����������� ����� (�� ���� ������� ������� � ��.)
```
// Constructor Functions and the new Operator
const Person = function (firstName, birthYear) {
  // Instance properties
  this.firstName = firstName;
  this.birthYear = birthYear;
  // �� ��������� ������ � ����������� ����� ������� - ��� ��� ��������� ������ ��� ����� �������!
  // this.calcAge = function () {
  //   console.log(2037 - this.birthYear);
  // };
};

// ����� ����������� ����� ��������� �������
Person.prototype.calkAge = function()
{
    log(2037 - this.birthYear)
}

// person.prototype ��� �� �������� ������������ person, � �������� ��� ���� ��������, ������� ������� ����� ����������� Person. �� ���� ��� ��������� ��������� � ������������� �������� 

const jonas = new Person('Jonas', 1991);
console.log(jonas);
```

��� ���������� ��� ������ ��������� new
1. ��������� ����� ������ ������
2. �������� ����������, this ���������� ���� �������� = {}
3. ������ ������������� ����� � ����������
4. ������� ������������� ���������� ������ {}

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

__������__
__species()__ : ���������� ���������� � ���������.
�������� �� ����� � ����� �������, � ����� ������������� �� �� ��������� (������)
Person.prototype.species = 'Human'
log(jonas.species) \\\ 'Human'

__hasOwnProperty()__ : ���������, ���� �� �������� � ������� 
log(jonas.hasOwnProperty'firstName')

##### 2. ES6 ������ : ���������� ��������� �������������, ���� ������� ���������� ��� ����, �� �� ���� ��� ��� �� �����������

������ ��������:
__Class expression__
`const PersonCl = class {}`
__Class declaration__
`class PersonCl {`
  `constructor(fullName, birthYear) {`
   ` this.fullName = fullName;`
   ` this.birthYear = birthYear;`
 `}`

������� �������:

> ������ ����� ��������� � .prototype property
  calcAge() {
    console.log(2037 - this.birthYear);
  }
  greet() {
    console.log(`Hey ${this.fullName}`);
  }
  get age() {
    return 2037 - this.birthYear;
  }

  > ���������� ��������, ������� ��� ����������
  set fullName(name) {
    if (name.includes(' ')) this._fullName = name;
    else alert(`${name} is not a full name!`);
  }
  get fullName() {
    return this._fullName;
  }

����������� �������:
1. ������ �� "�����������". ���� ��� �����-���������� �� �� ����� �������� �� ���� ��� ������������
2. ������ - ������� ������� (����� ���� ������������ � ������ �������� � ������������ �� ���)
3. ������ ����������� ������� ���� ���� ��������������� ������� �� ���� ������� (strict mode)

##### 3/ Obect.create() : ����� ������� ����� ��������, ����� �����������.
�� �������� ������������ ����� 1 � 2.
����� ������������ ��� ������������ ����� �������� (�����������)
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


__����������� ������__ : ������, ������� ������� � �������������, � �� � ������� ����������� (�� ���� ����������)

=======
getters\setters - �������, ��������� ��������, ������� �������� ��� ������ ������ � ������. ��� ��������� �������, � �� ������.
��������� ����������� ������.  

�get� � ��� ������ \ �set� � ��� ������
=======

������ 1:
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

������ 2: 
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
##### ������������ ������� \ ���������� 
***

__1. � ������������� ����� Object.create()__
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

> �������� ������ - ����� ��������� Student � ���������� Person.
��� ���������� �� ���������� ������� ��������� ����� �� ����������� �������� ��������

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

> ��������� �������� ������ ����� object.create, ��� ������������ �������� student ��������� �� �� ��� �� ����������� student ��� student, � �� Person. ����� ��� �������� ����� ������������ ��������� ��� 

```
Student.prototype.constructor = Student;
console.dir(Student.prototype.constructor);
*/
```

__2. � �������__
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

__3. ����� object.create()__
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
__������������: ���������� �������� � ������. ��������� ���� ������� � ������__
***
����� ��������� ����������� ��������� ����� ��������������.

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
## OBJECTS \ �������
***
���������  ������������ ����� - ������������\�������� (property=��������)

������
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
���
```
    calcAge:  function () 
    {
            return 2037-this.birthYear
    }
    // �� �� ����� ��� � ��� ����, �� � ���� ������ ��� ��������� �������� ������� �� ����������� ������ ��� ������
    calcAge:  function () 
    {
            return 2037-jonas.birthYear
    }
    // ����� ����� ���������� ���������� �������-��������� ������� � ����� �������� �������
    calcAge:  function () 
    {
            this.age = 2037-this.birthYear
            return this.age
    }
}
```

__���������� � �������� �������__:
1. ����� �����
`jonas.lastName`

2. ����� ���������� ������ 
`jonas['lastName']`
// � ���� ������ �������� ����� �������������� - ����� ����������� ����� expression 

__���������� �������� � ������__
`jonas.location = 'London'`
`jonas.['car'] = 'volga'`

__����� ������� (������) �� �������__
`jonas.calcAge(1991)`
���
`jonas.['calcAge'](1991)`

__THIS__ - �����, ������� ��������� �������, �� �������� ���������� ����� ��� ��������� �������, ����������� �����

__������ ������ JS__

  ��� ��������� ����������� ������ ��� ������ �������� � ������ stack ���������� ����� ������ � ���� ������� ����� �� ���� ����� ������� ����������. 
  
  ��� ��������� ������� ����� ������ (�������), �������� ������ � heap ����� �������� ���������� (������ �� ������ � ����� � ������), ������� �������� ������� � ������ � heap. ����� ������ ������ � ����� �� ����������, ����� ������ � heap �� ���������, ���������������� ����������� ������.
  ������ ������ ������ ������� �������� ���������. 
  
 ��� ����������� ������� (merge) ������������ ������� Object.assign, ��� ����������� �������� ��������� ������� ��� ����� ������ ������ (����� ������ �����������, � �� ����������� �������)
 ������
  `(const objectNewCopy = Object.assign({}, objectOld)`
 
 ���� ����� �������� ������ �� 1 ������ ��������.
 ��� deep clone ��������� ��������� �����.

__��������__
1. ���������� ��������� ���������
��������
const newObject =
{example: 123};

2. �� ES6 ����� �������� � ������ ��� ��� �������� ������ ������ ����� ���� (�� ������� ������ openingHours ���������� � ������ restaurant). ��� ����� �������� ���� �������� ����������. � ES6 ����� ������ ������� �������� - ��. � �������
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
  // �� ES6
  openingHours: openingHours,
  // ����� ES6
  openingHours,
};
```
3. ���������� ������� � ������
```
const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  // �� ES6
  moveSuitcase: function (one, two) 
  {
        alert("May I take your suitcase?");
        pickUpSuitcase();
        movie();
  }
  // ����� ES6
   moveSuitcase (one, two) 
  {
        alert("May I take your suitcase?");
        pickUpSuitcase();
        movie();
  }
};
```
3. ����� ������������ �������� ����������, � �� ��������� �� ����������
����� �������� �������� � ������ �� ������� (� �������, ��� ������) 
const weekdays = ['sun', 'mon', 'thu', 'fri']; 
```
const openingHours =
{[weekdays[1]]: '12-23',
[weekdays[2]]: '12-23',
[weekdays[3]]: '12-23'
}; 
```
��� ���
```
const openingHours =
{[`example day-${1+4}`]: '12-23',
}; 
```
__������������ �������__
����� ��� �������� �������� �������� ���������� ����� ��� � ����� ������� ���� ��� ��������.
� �������, restaurant.openingHours.sat �� ����� ����
����������, ����� �� � ������� ������� restaurant �������� openingHours.sat.open
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
��� ����� ����� ���������, ������������� �� �������� ����� ����� ����� ����� ���������
__��� ES2020__
```
if (restaurant.openingHours.sat.open)
{
    restaurant.openingHours.sat.open
}
```
__����� ES2020__ - ������������ ������� (?.)
`restaurant.openingHours.sat?.open`
������ ���� sat �������� open ����� �����������
���� sat undefined ��� null ��������� ����� ����� undefined ��� null, � �� ������ ���� �� ����� ��� ��� ����� ���������.
����� ������������ ����� ���������� �����
`restaurant.openingHours?.sat?.open`
     
������:
```
const days = ['sun', 'mon', 'thu', 'fri']; 

for (const day of days)
{
// ���������� ������ ��� day ����� ��� ��� ��� ��� ����������. || ''closed - ������������� �������� �� ��������� - ���� open �� ��������� �� ����� �������� ��� �������

    const open = restaurant.restaurantOpeningHours[day]?.open || ''closed
    log (`On ${day} we open at ${open}`)
}
 ```
 �� ���� �������� ����� 0 �� ����� ��� �� ���������.
 ��� ����� ����� "�������" ��������
 ������
   `const open = restaurant.restaurantOpeningHours[day]?.open || ''closed`
���
   `const open = restaurant.restaurantOpeningHours[day]?.open ?? ''closed`

������������ ������� �������� � � ��������
� �������, (order ��� �������)

`restaurant.order?.(0.1) ?? '����� ����������'`

�������� ����� � ���������
`const users = [{name: 'My name', email: 'myemail@mail.io'}]`
`users[0]?.name ?? '������ ������'`

***
#### ���� � ��������
***
����� ������� ����� ��� ����� ����.
����� ����������, �� �������� ��� ��� �� ��� (���������� ���������� keys).
����������� ���� for of, ����� ����� ������, �� � ���� ����� �������� ������ ������

1. ��� ����������� ����� �� ��������� ������� 

//�������� ������
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
// ���������� properties ����� �������� �� ������� �� ���������� �������. 

// ����� �� ��� �������� ������ (������ Object.keys(openingHours) ��� ����� ������������ properties
```
for (const day of Object.keys(restaurant.openingHours))
{ 
log(day)
}
```

// ����� ����� �������� ���� ���
```
const properties = Object.keys(restaurant.openingHours)
let openStr = `�� ������� ${properties.lenght} ����: `
for (const day of properties)
{ 
    openStr += `$day, `
}
```

���������, ��� � ���������� openStr ����� ��������� ����� ����������� �������� ������� ���������, ������ ��� ����� ���� ������.  

2. ���� �� ��������� ������� (values)
`const values = Object.values(openingHours)`
// � ��������� ����� ��� � ���������� ������

3. ����� �������� � �������� � �������� �������� ����� ������������ ����� entries. �� ���������� ����� �������� � ���� ��������.
```
const entries = Object.entries(openingHours)
for (const x of entries)
{
    log(x) - ������� ������ � ������� ��� �������� � �� ��������
}
```
����� ������������ ��� �� �������� ����� ������������ ������ x ����������������. ��������� ������ ������� �������� ������������ {}.
� ����� ������� ������ ����� ���� �� ������ ������������ ����� ��������� [day, values]
```
for (const [day, {open, close}] of entries)
{   
    log(`On ${day} we open at ${open} and close at ${close}`)
}
```
������ ������
```
for (const [goalNumber, goalPlayer] of game.scored.entries())
{
    console.log(`Goal ${goalNumber + 1}: ${goalPlayer}`);
}
```
���������
`game.scored.entries()` - ������������ ��� �������
`Object.entries()`- ������������ ��� �������

***
#### �������� ������� JS
***

������:
```
var houseKeeper1 = 
{
    yearsOfExperience: 12;
    name: "Jane";
    cleaning: ["bathroom", "lobby", "bathroom"]
}
```
������� - ����������� ��������. ������ ����� �������� ����������� ���������.
```
function BellBoy (name, age, hasWorkPermit, languages)
{
    this.name = name;
    this.age = age;
    this.hasWorkPermit = hasWorkPermit;
    this.languages = languages;
}
```
�������������:
```
var bellBoy1 = new BellBoy("Timmy", 19, true, ["French", "English"]);
```
