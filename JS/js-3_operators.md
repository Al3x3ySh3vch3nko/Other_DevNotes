## ????????? JS
***
#### 1. AND (&&) \ OR (||)
***

???????????:
1. ????? ???????????? ????? ???? ??????.
2. ????? ?????????? ????? ???? ??????.
3. "???????? ?????????"

???????????? ???:
1. c???????? ? ????????? ??????? ????????
2. "???????? ?????????" - ????????? ?? ?????? ??????? ????????.

### "???????? ?????????"
__??? ????????? OR__ - ?????????? ?? ?????? "????????? "????????. ???? ??? ?????? - ?????????? ????????? ? ?????? ?????????.

?????? ?????????????
??????:
```
const numGuests = 23
const guest1 = numGuests ? numGuests : 10;
```

????????????:
```
const numGuests = 23
const guest1 = numGuests || 10
```

?? ????? ???????? ????????, ???? ???????? ????? 0 - ? ???? ?????? ?????????? 10 ??? ??? 0 ??? ?????? ????????.

??? ????, ????? ????????? - ???????????? "???????" ????????. ? ??? 0 ? ?????? ?????? ?? ????????? ??????? ??????????, ??????? ????????? ?????? undefined ? null
```
const numGuests = 0
const guestCorrect = numGuests ?? 10
(?????????? 0 ??? ??? ?????? ??? ?????????)
```

__??? ????????? AND__ - "??????????" ?? ?????? ?????????? ?????? ????????. ???? ??? ???????? ????????? ?????????? ????????? ? ?????? ?????????.
???????????? ?????????? - ?????????, ???? ???????? ??? ??????? ????????.

??????.
??????:
```
if (restaurant.orderPasta)
{
    restaurant.orderPasta('pasta', 'tomato')
}
```
????????????:
```
restaurant.orderPasta && orderPasta('pasta', 'tomato')
```

***
#### 2. NOT (!)
***
1. ??????? ???????? ???????? ? ??????????? ???? true/false.
2. ????? ?????????? ??????????????? ????????.

***
#### 3. ????????? ????????? == \ ===
***

== - ??????????? ??? ?????? ? ?????????? ??????????????? ?????? (?????? ?? ???????). ?? ????????????? ????????????
=== - ??????? ???????????? ?? ?????? ???? ??????

***
#### 4. SWITCH : ???? ???? ????????? ??????? if ?? ??????? ???????????? ??? ???????
***
```
day = '??'

switch (day)
{
case '??': 
    console.log('??????? ??-??')
    break;
case '??':
    console.log('??????? ??-??')
    break;
case '':
case '??:
case '??:
    console.log('??????? ??-?? ??? ?? ? ??')
    break;
default:
    console.log('???? ?? ???? ?? ???????? ?? ????????')
    }
```

***
#### 5. ????????? ????????
***

```
const age = 18
age >=18 ? yes : no

const age = 18
age >=18 ? console.log (`I like drink wine`) : console.log (`I like drink water`) 
```

????????? ???????? ????? ????????? ??? expression ? ????????? ?? ?????????? "??????" ?????????? 

const age = 18
const drink = age >=18 ? `drink wine` : `drink water`) 

> ??? ????????????? if\else ???????? ??:

let drink2
if (age >= 18) 
{
        drink2 = `wine`
}
else
{
    drink2 = `water`
}

????????? ???????? ????? ???? ??????????? ? ????????, ? ??????? ?????? ???????????? statement ???? if\state 
const age = 18
console.log(`I like to drink ${ age >= 18 ? 'wine' : 'water'}`)
