
***
## ����������������
***

#### ���������������� ��������

��������� ������
  
`const arr = [2, 3, 4]` 
  
��� ����, ����� ��������� ��������� ������� ���������� ��� ����������������
  
  `const a = arr[0]`
  `const b = arr[1]`
  `const c = arr[2]`
  
__��� ����� ����������������__
  
  `const [a, b, c] = arr;`
  
  ����� ���������� ������ � ������� � ��������������������� ���������� ����� ������� ������
```    
  const restaurant =
}
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
};

const [first,  , third] = restaurant.categories
```

__����� �������� ������� ����������__ 
```
[first, third] = [third, first]
```
����� ����������� �������� = ������ �� �� ������� ��� ���������� 

__����� �������� �������� �� ������� ����� ������� ����� ����������������__
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

restaurant.order(2, 0)  - ���������� �������� ���� �� �������� starterMenu � mainMenu, ������� ��������� ��� ��������� 2 � 0.

����� �������� �� � ��������� ���������� � ����� �� ������� ����� ����������������

const [starter, main] = restaurant.order(2, 0) 
```

__����� ����������������� ��������� �������__ 
```
const nested = [0, 2, [5, 6]]

[a, b, [c, d]] = nested 
```

__���� ����� ������ ���������� ����� ����������� �������� ���������� ����� ����������������, ������� ��� ����� ��������� �� ���������__
```
[a=1, b=1, c=1] = [4, 5]
```
� ���� ������ c ����� ��������� �� undefined � 1

������ ���������������� �������
```
const animals = [
  { name: "cat",
  sound: "meow" },
  
  { name: "dog", 
  sound: "woof" }
];
const [cat, dog] = animals;
```

#### ���������������� �������
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
����� :
������� ���������� �� ����� ��������, �� ����� ����� ������������ �������� ���������� 
`const {name, openingHours, categories} = restaurant;`

__����� ������ ����� ��� ��� ����������-��������� �������, ����� ������� �� ����� ���������__
```
const {name: RestaurantName, openingHours:restaurantOpeningHours, categories: RestaurantNameMenu} = restaurant;
```
__��� ����, ����� ������ �������� �� ��������� ���������� ������� � ���� �� ����� ����� �����:__
��������� ����������, � ��� � ������� ������ �������� ���������, ����� ��������� ���� ����� - ����� ��� ����������, �  ���������� ������� �������� �� ���������
`const { starterMenu: starters = [defaultValue]} = restaurant;`
���� � ���������� ������� �� ������� ������, � � ��������� ���� �������� � �������, �� ��� � ������������ �� ���������.

__������� ��������__
�������� �� ���������
```
let a = 111;
let b = 999;
```
�������������� ���������� � �������
`const obj = { a: 23, b: 7, c: 14 }`

������� �������� ���������� ����� ����������������
`({ a, b } = obj);`
��� ������� ������ ��� �������� �� ����� ! ��� ����� ��� ����, ����� ������ js �������, ��� ��� �� ���� ����, � ����������������

__��������� ������� (��. ������ restaurant ����)__
���������� �������� �� ������� �������, ��� �������� ����� ������� ����� ��������� � ������� ����������� ��������� ��� ��� �������
`const { fri: {open, close} }  = openingHours;`

__��� ���������� �� ���� ��� ����������� ����� ���������__
`const { fri: {open: openHour, close: closeHour} }  = openingHours;`

__��� ���������������� ���������� �������__
(���������� ���� ��������, �� 3�� ����������� �������, ������� ����� �������������������. ��� ���� ������� ����� ���� ������������.)
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

__����� ���� �������� ��������� ������� (��� �������)__

`const [red, green, blue] = [9, 33, 456];`
`console.log(green) ����� 33.`

������ ���������������� ������� (����� ����, ��� �� ��� ������� � ������� ��� ���������� cat)
`+const {name, sound} = cat;`
name � sound ������������� cat.name � cat.sound

� ������� �������� ���������� ������ ��������� � ��������� ��������������������� ����������.
����� ������ ����� �������� ����� ������� �� ����� ���������:
`+const {name: catName, sound: catSound} = cat;`

��� ������������ �������� �� ��������� 
`const {name = "Tysya", sound = "Meow"} = cat;`

__��������� �������:__

�������� ������ (���������� cat �������� � ���� �����):
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
���������������������:
```
const { name, sound, feeding: {food, water} } = cat;
console.log(food) === 2
console.log(water) === 3
```

#### ���������������� � ��������

�������:
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
����������������:
```
const{animal, makeSound} = useAnimals(cat);
makeSound ����� �������� � �������� ����������.
```

======= �������� ���������������� =======
\\ ���� � �������
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
��� � ������� � �������
���������������� ������� 1 ������
`const [honda, tesla] = cars;`
���������������� � ���������� ����� ��� ���������� "��������"
```
const {
  speedStats: { topSpeed: hondaTopSpeed }
} = honda;
const {
  speedStats: { topSpeed: teslaTopSpeed }
} = tesla;
```
���������������� � ���������� ����� ��� ���������� "����"
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
## Spread operator : ��������� ���������� �������, �������� ��� �������� ������� �������� ��� ���� �� �� ���� �������� ������.
***

�������� �� ����� ������������ ����������, �� �� ���������.
(�������, ���, ������, set-�������)

����� ��� �������� ������� � � ������� �� ���������������� �� ������� ����� ����������, � ������ "���������" � ���������� ������ ��� ����� �������� �������� � �������

�������� ������
`const arr =  [7, 8, 9]`

��� �����-��������� ������� ����� ������ � ������� 1 � 2 � ������ � �������� ��� �� ������� arr 
`const badNewArr = [1, 2, arr[0], arr[1], arr[2] ]`

�� �����-����������
`const newArr = [1, 2, ...arr]`

��� �����-��������� 
`[1, 2, arr]` ������ arr ��� �� ������� ��� ������ � �� ���������� ����������

���� ������������ ������ newArr ��� �����-���������, �� � ������ ����� � ���� �������
`console.log(newArr)`

���� �� �����-���������� �� �� ����� ��� ��������� �������� ����� ������
`console.log(...newArr)`

�������������:
- ����������� �������
`const copyArray = [...oldArray]`
- ����������� ��������
`const mergeArray = [...firstArray, ... secondArray]`

__�������� �������� � ������� ����� �����-��������__
````
const orderPasta = function (ing1, ing2, ing3)
{
console.log(`This is a pasta with ${ing1}, ${ing2}, ${ing3})`
}
const ingridients = [a, b, c]
orderPasta(...ingridients)
```
C ��������� �����-�������� �������� ���
��� ���������� ��������
```
const restaurant =
{
    menu: [pizza, salad],
    time: '06:00 - 00:00',
}
const new restaurant = {...restaurant, founder: ''Aaron,}
```

��� ����������� ������� ����� �����-��������.
������ ��� ���� ���������� - �� ����, ��������� �����.
`const restaurantCopy = {...restaurant}`

***
## Rest operator : �������� �� spread, ���������� � ������ ��������
***

������������ ����������:
1) ��� ����������������
������ rest (����� �� ����� ����������)
```
const [a, b,  ...others] = [1, 2, 3, 4, 5]
```
(�������� 3, 4, 5 ����� �������� � ���������� others � ���� �������)

��� ������
`const array = [1, 2, 3, 4]`
����� ��������� ������� �������� (1) �� ������� ���������� one
� ��������� �������� � ������ ���������� others 
`const [one, ...others] = array`

� ������� - ��������� �����.
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
� ���������� weekdays ������� fri � thu

2) �������� �������� � �������
����� ���������� ������� ���������� �������� � ������� (���������������) ����� ������������ ���� ��������
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
� ������ ������ ������ ������� ��������� ����� ������������ � ���� ������� � ����� ����������  

����� �������� ������ ��� �������� ������� 
```
const x = [23, 5, 7]
add (...x)
```
