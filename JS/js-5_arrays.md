***
## ARRAYS \ �������
***
***
#### 2 ������� ��������
***
1. const ages = [1234, 1222, 4245]

2. const ages = new Array(1234, 1222, 4245)

> � ������ ����� �������� �������������� ��������, � ��� ����� ����� ������� - ��� ��� �������� expression
`const ages = [15*6, 674637+4664, 5657-6464]`
�
`const years = [1099, 1094, 2002, 2018]`
```
const calcAge = function (birthYear)
{
    return 2077 - birthYear
}
const ages = [calcAge(years[0]), calcAge(years[1]) ]
```

> � ������ ����� �������� ������������ ����� ����������
`const age1 = 456`
`const ages = [age1, 545+4664, 5657-6464]`

> � ������ ����� �������� ������ ������� 

> � ������ ����� �������� ������ ���� ������

> � ������� ������ ������ ������� � �������������� ������ �������, ������ � ��� ���������

***
#### __������ ��������__
***

__push()__ : ��������� ������� � ����� �������   
`���������������.push('�������� ��������\������')`

__unshift()__ : ��������� ������� � ������ �������
`���������������.unshift('�������� ��������\������')`

__pop()__ : ������� ��������� �������
`���������������.pop('�������� ��������\������')`

__shift()__ : ������� ������ �������
`���������������.shift('�������� ��������\������')`

__indexOf()__ : ���������� ����� �������� � �������
`���������������.indexOf('�������� ��������\������')`

__includes()__ : ���������� true\false ���� ������� � ������� ��� �� � �������. ���������� ������� ������������
`���������������.includes('�������� ��������\������')`

__slice()__ : �������� ����� ������� ��� ��������� �������, ������� �����.
`arr.slice (��������� �������)`
`arr.slice(2)` \\ �� ������� ������� �� �����
`arr.slice(2, 4)` \\ �� ������� �� ���������� �� ������� ���������
`arr.slice(-2)` \\ ��� ���������
`arr.slice(-1)` \\ ��������� �������
`arr.slice(1, -2)` \\ c ������� �� ���� ���������
`arr.slice()` \\ ������ ����� ������� - ������ spread [...arr]

__splice()__ : ������ slice, �� �� �������� ����������� ������ - ������ �� ���� ���������� ��������.
������������� ����� �� ��� slice.
�� �������� ������������ ��� �������� ��������� �� �������.
��� ���� �������� � ������ ��������.
`arr.splice(1, 2)` \\ �������� � ��������� ������� � 1 = ������� 2 = ��� �������� (���������� ��������� ��� ��������).

__reverse()__ : ������ (��������������) ������� ��������� � �������. �������� ������������ ������.

__concat()__ : ���������� �������, �� �������� ������������ ������
`const letters = array1.concat(array2)`
������������ ����� ����������������
`[...array1, ...array2]`

__join()__ : ������� ������, �������� ������� ��������� �������� ��������
`array.join( ' + ')`

***
__�������� �������� ����������__
***

����� �����������
`const x = new Array(7)` \\\ ������� ������ ������ � 7 ����������

���������� 
\\ ����� fill() (�������� ������)
`fill(1)` - ��������� ������ ��������� 1
`fill(1, 3)` - ��������� ������ ��������� 1 � �������� �������
`fill(1, 3, 5)` - ��������� ������ ��������� 1 � �������� �� ����� ������ 

\\Array.from() - �����, ����������� � ������� Array.
`Array.from({length: 7},  () => 1)` \\ ������� ������ ������ 7 � ��������� ��� ��� ���� �� ���������� ����� map ������ 7

`Array.from({length: 7},  (currentElement, i) => i + 1 )` \\ �������  ������ ������ 7 � ��������� ��� ������� ������ + 1 �� ������ ��������

_������� ������������ ������������� - �������� ������� �� ��������������� ���������_
��� ���� ������ - �������� ����������� ������� ����� ����� �������� � ����� ������

***
#### LOOPS ����
***
__1.FOR__ - �������� �� ��� ���, ���� ������� �� ������ false. ���������� ������� 1 ���

// ������
```
console.log('1')
console.log('2')
console.log('3')
console.log('4')
console.log('5')
console.log('6')
```
// ����
```
for (let rep = 1; rep <=6; rep++)  
{
    console.log(rep)
}
```

// ���� FOR ��� �������� �������� 
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
//���
```
for (i=0; i<=jonas.length; i++)
{
    console.log(jonas[i] typeof jonas[i])
}
```

// ������ ���������� �������� �� ������ ������� � ������ ����� ����
```
const type = []
for (i=0; i<=jonas.length; i++)
{
    // ������ ������ �������
    console.log(jonas[i] typeof jonas[i])

    // ������ ���������� ������� ���������� ����������
    types [i] = typeof jonas [i]

    // ������ ���������� ������� ������� push
    types.push(typeof jonas[i])
}
```
// ������ �������� �������� � ������� � ���������� �� � ����� ������
```
const years = [1991, 2059, 2077, 1969]
const ages = []

for (let i = 0; i <= years.length; i++)
{
    ages.push(3000 - years[i])
}
```
// CONTINUE STATEMENT - ������� �� ������� �������� � ���������� ��������� � ������ �����
 � ������� � ������� ��������� ������ �� �������� �������, ������� �������� �������� 
```
for (i=0; i<=jonas.length; i++)
{
    if (typeof jonas[i] !== 'string') continue
   
   console.log (jonas[i])
}
 ```
 
// BREAK STATEMENT - ���������� ����
� ������� ���� ���� ������������ ��� ���������� ���� ������ - �����
```
for (i=0; i<=jonas.length; i++)
{
    if (typeof jonas[i] === 'number') break
}
```

// ������ - �������� ����
```
for (let i = jonas.length - 1; i >= 0; i--)
{
    console.log(jonas[i]);
}
```
// ������ - ���� ������ �����. ������� 3 ���� �� 5 ����� ������ �������.  
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

���������� exercise �������� �� ������ �����

__2. WHILE__ - ������� �������, �� �� �������. �������� �� ��� ���, ���� ������� �� ����� false. �� ����, ����� �������� ��� ��������, ���������� ���������. ���� �� ����� ������� ������� ���� ������� ���������� false.

// ������ ������ �����
```
for (let rep = 1; rep <=6; rep++)  
{
    console.log(rep)
}
```
// �����
```
let rep = 1;
while (rep <= 10)
{
    console.log(rep)
    rep++
}
```

// ������ ������������� ����� ��� ��������. ������ - �� ��� ���, ���� ����� �� �������� ����� 6 ������ �����
```
let dice = Math.trunc(Math.random() * 6) + 1
while (dice !== 6) 
{   
    console.log(dice)
    let dice = Math.trunc(Math.random() * 6) + 1 // ��������� ����� ���������� ��� ����, ����� �� ���� ������������ ����� ��� ��� � ��������� ������ ����� ���������������� ������ ����������
}
```

__3. FOR - OF__ - ��� �������� ��������

��� ������
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

������ ������
```
const menu = [...restaurant.starterMenu, ... restaurant.mainMenu] 
```

�������� for - of loop

`for (const item of menu)` \\ ��� ��������� � ������� item ������� �������� ������ ������� ������� menu
����� ������������ break � continue. �� �������� � ��������� ���������. 
����� �������� ������ ���������
```
for (const item of menu.entries())
{
    � ���� ������ item ������ ����� �������� ������ ��� ������ ������� ������� � �������� ��� ������
    
    ����� ������� "�������" ���������:
    
    log(`${item}[0] + 1: ${item[1]}`) 
}

��� ����� ����������������� �� ����� ��� ����������

for (const [index, element] of menu.entries())
{
    
}
```

__4. forEach__ ��� ����������� �������
(!) ������ �������� ��� for of.
�� ������� ����� ������.
```
const movements = [100, 300, 485, -309, -453, -3444, 4555]
 \\--- ������ � for of

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
 
 \\--- ������ � forEach
 
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

\\--- ������ � for of ������ �� ���������
  
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

\\--- ������ � forEach ������ �� ���������

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

 \\\--- forEach ��� maps
 
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
 
\\\--- forEach ��� sets
 
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
    console.log(`${value}: ${value}) \\ key ����� ����� �� �������� ��� � value, ��� ��� ��� set
}
```
***
#### ���������� ��������
***
������
__sort()__ - ��������� ������ �� ��������� ������ ��������. (!) �������� ������������ ������. 

����� ����������� ������ ��������� �� ����� �� �������� � �������� ��� ��������, ��������� � ��� ����� �� ������������� ��������
�� �������� � ��������
```
array.sort((a, b) => 
{
    if (a > b) return 1
    if (b > a) return -1
})
```
���
```
array.sort((a, b) => a - b))
```
�� �������� � ��������
```
array.sort((a, b) => 
{
    if (b > a) return -1
    if (a > b) return 1
})
```
���
```
array.sort((a, b) => b - a))
```
***
#### ������������� ������� � �������
***
// ������
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460],
const eurToUsd = 1.1
const totalDepositsUSD = movements.filter(mov => mov > 0).map(mov => mov * eurToUsd).reduce((acc, mov) => acc + mov, 0)
```
//�� ����� ��������� ��� ������ ������ � ���, ������� �� ��� ���������� ������. � ������ ������ reduce �� ���������� ������, � ��������

***
#### ������� �������
***
__filter()__ : �������� ������ �������, ���� ������ ������� ���������� true.

�������� ������
`var numbers = [3, 56, 2, 48, 5];`
����� ������������� ������ � ������� ������ �� ��� ������ 10: 
```
const newNumbers = numbers.filter(function(num)
{
return num < 10;
}
```
������ 2
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460],

const deposite = movements.filter(function (mov)
{
    return mov > 0
})
```
�� �� � for of
```
const depositsForOf = []
for (const mov of movements) if (mov > 0) depositsForOf.push(mov)
```

__reduce()__ : ������������ ������, ����� ���-�� � ������ �� ���

�������� ������
`var numbers = [3, 56, 2, 48, 5];`

����� ����� ���� ����� � �����, �������� �� �������, ��������� ��� ������� ���� �������� � ����� ����� ������ �������� - 
```
var newNumber = numbers.reduce(function(accumulator, currentNumber)
{
 return accumulator + currentNumber;
});
```
� ������ ������ accumulator �����  �������� ������� ����� 3, currentNumber ������� - 56, ��� ������������. �� ��������� �������� - ����������� ������ ������ ����� ���������� ������ ������ ����.

������ 2 (������ ������� ���������� ������, � ����� �������� ������������ ������ � �.�.)
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460],
const balance = movements.reduce(function (accumulator, currentValue, index, array) 
{
    return accumulator+currentValue
}, 0 ) \\ ��������� �������� accumulator
```
��������� arrow 
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460]
const balance = movements.reduce((accumulator, currentValue, index, array) => accumulator+currentValue, 0 ) 
```
�� �� � for of
```
let balanceForOf = 0;
for (const mov of movements) balanceForOf += mov
```
���������� ������������ ����� � �������
```
const movements = [200, -200, 340, -300, -20, 50, 400, -460]
const max = movements.reduce((acc, mov) => 
{
    if (acc > mov) return acc 
    else return mov
}, movements[0])
```

__find()__ : ���������� ������� �������� true (���� ������ ���������� � ������� � ������� ���)

�������� ������
```
var numbers = [3, 56, 2, 48, 5];
const number = numbers.find(function (num)
{
    return num > 10; 
});
```

������� 56 ��� ��� ��� ������ ������ 10

���������� ���
```
var numbers = [3, 56, 2, 48, 5];
const numberBiggerThan0 = numbers.find(num => num < 0)
```
������� �� filter
1) ����������, ������ ��������, � �� ���
2) ���������� ��������, � �� ������

������ ������ ������� � �������, ���������� ������ ������� - �� ���������� ��������� �������
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

__findIndex()__ - ���������� ������ ������� ��������, ������� ������������� �������. �������� ��� find
����� �� ����� indexOf, �� � indexOf ����� �������� ������ �������   �������� (���������� �� ��� �������� � ������� ��� ���)

__SOME()__ �����, ����������� ��������� �������. ���������� ������� �������� - "�������� �� ����� ������".
������� �� includes() �� ��� includes() ��������� �� ������ ������������ ������ ����������� �������� �������, � some ��������� ��������� ����������� �������.
```
const numbers = [3, 56, 2, 48, 5, -5, -38];
const anyDeposits = numbers.some(num => num > 0)
```
__every()__ �����, ������� �� some() � ����������� ��������� �������. ���������� ������� �������� - "�������� �� ��� �������� ������� �����".
__flat()__
������� �� ������� � ���������� ��������� ������ ������. �������� � ���� ������� ����������� �� ���������.
```
const array = [[1,2] 3,4]
array.flat() \\ 1 ������� �����������
array.flat(2) \\ 2 ������ �����������
```
__flatMap()__
�����, ����������� map + flat � �����. �������� ������ �� 1 ������ �����������

