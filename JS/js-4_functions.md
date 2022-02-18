***
## �������
***

�����:
��� �������������� ������ ������� ���������� ��� �� ������ ���� ���������� ��� �������. 
��� ������� �������� ��� �� �������� ������ ������� ��� �������� ��� ������

```
function getMilk()
{
    alert (get milk);
}
```
�����
```
getMilk();
```

___��������� � ��������� �������___

```
function getMilk(money) \\ money - ��������
{
    alert ("Move right");
    alert ("Move straight");

    var numberOfBottles = Math.floor(money * 1.5);

    alert ("Get" + numberOfBottles + "milk");
    alert ("Get milk");
}

getMilk(12); \\ 12 - ��������
```

***
#### ������� �������� �������: DECLARATION \ EXPRESSION
***

 __[ ! ] �������� ������� ����� ����: �������, ����������� ��� Function Declaration, ��������� ��������������� �� ���������� ����.__

__1. DECLARATION__ : �� �������� � ����������, � ��������� �������. ����� ������� �� �� ����������
```
function calcAge(birthYear)
{
    return 2037 - birthYear
}   

// �����
const age = calcAge (1986)
```

__2. EXPRESSION__ : �������� � ����������, ��� �������� �������. ������ ������� �� �� ����������
```
const age = function (birthYear)
{
    return 2037 - birthYear
}

// �����
const age = calcAge (1986)
```

***
��������� �� ��������� (����� �����)
***
```
const age = function (
birthYearA = 1999 ���
birthYearB = 1999-234 ���
birthYearC = birthYearB -234)
{
    return 2037 - birthYear
}
```

����� ���������� ���� �� ����������, ������� ���������� � ������� ��� ����� �������� �� ���������, �� ��� ������ ������� ��� �� ����� ����������� - ��� ��� ������ ������� ����� ������� ��� undrfined   

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
#### ������� 1 ������ � ������� ������� �������
***
__������� 1 ������__ : ������� � ���� ���������, ��� ������� ������� � JS ����� ���� ����������� (��� �������� ���������) � ������ - ������������ � ������ ������� ��� ������������ �� ������ �������.

__������� ������� �������__ : ������� � ���� ������������ ���������� - �������, ������� ��������� � ���� ��� ���������� � ���� ������ �������.

__����� �������__
__1. "�������" �����__
�������, ������� ����� ���������� ������ ������ �������__
```
function cutFruitPieces(fruit)
{
    return fruit * 4
}
```
�������, � ������� ���������� 1 �������
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
1) ����������� �� �����, � ��� ������ ������ �������,
2) �������, ������������ callback ��� ������� ������� �������

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

// Higher-order function *******(fn - ������� - callback)*******
const transformer = function (str, fn)
{
  console.log(`Original string: ${str}`);
  console.log(`Transformed string: ${fn(str)}`);
  console.log(`Transformed by: ${fn.name}`);
};

transformer('JavaScript is the best!', upperFirstWord);
transformer('JavaScript is the best!', oneWord);
```


__3. ������� ���������� �������__
```
const greet = function (greeting)
{
    return function (name)
    {
        console.log(`${greeting} ${name}`)
    }
}
```

�����:
���� 1) `const greetingHey =  (`Hey`)` \\ ��������� ��� ������ � ���������� greeting ����� `Hey`
���� 2) `greetingHey(`ALex`)` \\  ���������� ������ `Hey Alex`

������ �������������� ������
`greet (`Hello`)(`Alex`)` \\ ���������� ������ `Hello Alex`

***
// Immediately Invoked Function Expressions (IIFE)
***

�������, ������� ����������� ������� � ����� ������� ����� 
����� �������������� ����� ������ ������ �� ������� ���������, ������ � ����������� ����������������
�������:

__IIFE - ������� �������__
```
(function () {
  console.log('This will never run again');
  const isPrivate = 23;
})();
```

__IIFE - ���������� �������__
(() => console.log('This will ALSO never run again'))();

***
### ���������� ������� \ ARROW FUNCTIONS
***
������ 1.
������
```
function calcAge1(birthYear)
{
    return 2037 - birthYear
}
```
��� (1 �������� � 1 ������� ��������)
```
birthYear => 2037 - birthYear
```

������ 2.
```
const movementsUSD = movements.map(function(mov)
{
    return mov * eurToUsd
}
```

�� �� ����� � arrow function
```
const movementsUSD = movements.map (mov => mov * eurToUsd)
```

> c��������� � ����������:
```
const calcAge = birthYear => 2037 - birthYear
```

> ����� (� ��������� � ����������):
```
const age = calcAge(1991)
```

> (���� �������� � ��������� �������)
```
const yearUntilRetirement = birthYear => 
{
    const age = 2037 - birthYear
    const retirement = 65 - age
    return retirement
}
```
> (��������� ���������� � ��������� �������)
```
const yearUntilRetirement = (birthYear,  firstName) =>
{
    const age = 2037 - birthYear
    const retirement = 65 - age
    return `${firstName} retires in ${retirement} years`
}
```
> �������, ������������ ������� � ���� ���������� �������

�������� 
```
const greet = function (greeting)
{
    return function (name)
    {
        console.log(`${greeting} ${name}`)
    }
}
```

����������
```
const greetArrow = greeting => name => console.log(`${greeting} ${name}`)
```

> ������� � ���������� ������� (� ��������� ����������)
�������
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
����������
```
const calcTip2 = billValue => billValue >= 50 && billValue <= 300 ? billValue*15/100 : billValue*20/100

const tip1 = calcTip1(bill)
const tip2 = calcTip2(bill)
console.log(`The bill was ${bill}, the tip was ${tip1}, and the total value ${bill + tip1}`);
console.log(`The bill was ${bill}, the tip was ${tip2}, and the total value ${bill + tip2}`);


***
__������ call(), bind(), apply()__ : ��� ������ ���������� ��� ����� �������� �� ��������� this
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

��������� ���������� book, � ������� �������� ������� �� �������, �� ��������� ��������� �� �������, � ������� ���� ���������� �������, ������� ����� �� ���������, ��� ��� ����������� �������� this � ���� �������, � ��� �������� ��� ���������� � ����� ����������. 

��� ����� ������������ ������ call \ apply \ binds.
��� ������ ���������� ��� ����� �������� �� ��������� this

***
__ Call() __
***

`book.call(eurowings, 23, 'Sarah Williams');` \\ ������ ���������� �������� ������ "������� ���������", ����� ������� ������ �� ������, �� ���� ������������� � ���� ����� ������� this.
�� ����, ����� ���� ����� �������������� �� ������� �������, �� �������� �� ������ � ��� �� ������� ������ (� ������ ������ ������� book ���� �� ������� ������� lufthansa, �� ��������� �� ���������� ������������ � ������ eurowings).

!��� ���� �������� �������� �������, � ������� ������������ �������� ������ ���� ���������� �� ���� �������� - �� �������� ������� ���������� ��� � � ������� ������������!

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

Apply method - �� ����� ���� ���������� �� ������� ��� ��� ������ book ����� book.call(swiss, 583, 'Mary Cooper'), � ����� �� �� �������. �� ����������� ������ ��������� ����� (���������� ������� call �� spread ���������� - ��. ����)
```
const flightData = [583, 'George Cooper'];
book.apply(swiss, flightData);
console.log(swiss);
```

� ����������� JS ����� ��������� � �������� apply() ������� call() ��������� spread ��������
��� 
`book.call(swiss, ...flightData);`
***
bind()
***
�� �������� ������� �����, � ��������� �������, ��� this ����������

```
\\ ������ ������
book.call(eurowings, 23, 'Sarah Williams');
book.call(lufthansa, 23, 'Sarah Williams');
book.call(swiss, 23, 'Sarah Williams');

\\ ������� ������������ � ����������
const bookEW = book.bind(eurowings);
const bookLH = book.bind(lufthansa);
const bookLX = book.bind(swiss);

\\ ����������
bookEW(23, 'Steven Williams');
bookLH(23, 'Steven Williams');
bookLX(23, 'Steven Williams');

\\ ��� ������� ������ ��� ���������� ���������� (���� ����������) ��� ����������� �� �������. � �������, 23 ���� ������� �� ���������

const bookEW23 = book.bind(eurowings, 23);

\\ �����
bookEW23('Jonas Schmedtmann');
bookEW23('Martha Cooper');

\\ ������ �  Listeners
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  console.log(this);

  this.planes++;
  console.log(this.planes);
};

document
.querySelector('.buy')
.addEventListener('click', lufthansa.buyPlane.bind(lufthansa)); \\ ������������ bind ����� ��� �������� �� ������ ������� ����� this

// Partial application - ����� bind ������������ � ������ ������� ��� ������������ �������� ��������, � �� ��� ����������� this

const addTax = (rate, value) => value + value * rate;
console.log(addTax(0.1, 200));

const addVAT = addTax.bind(null, 0.23); \\ rate ��������������� � 0.23 ������.
��������� this � ������ ������ �������, �������� � ������� �������� ��������������� ��� null
�� �� ����� ��� � 
addVAT = value => value + value * 0.23;

console.log(addVAT(100));
console.log(addVAT(23));

// ������������� �������, ������������ ������� ������ ���� ����

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




