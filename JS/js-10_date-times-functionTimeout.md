***
## DATES \ TIMES
***

moments.js - ���������� ��� �������

__������� ����������� �������__
let now = new Date()

__��������� ������ � ����������� ��� �� �������������������__
```
new Date ('December 24, 2015') 
new Date (2037, 10, 19, 15, 23, 56) \\ ����������� ������ � ������ ���� � �������. � JS ����� ������ ���������� � 0!
```

__�������� ����� ������� Unix-�������__
new Date (0) \\ 1 ������ 1070 �.
new Date (3 * 24 * 60 * 60 * 1000)  \\ �������� 3 ��� � Unix-�������( � �������������) 

__�������� ��� \ ����� \ ���� \ ���� ������ \ ���� \ ������ \ �������__
```
const future = new Date (2037, 10, 19, 15, 23, 56)
future.getFullYear()
future.getMonth()
future.getDate()
future.getDay()
future.getHours()
future.getMinutes()
future.getSeconds()
```

__�������� ������ � ������� ISO__
```
future.toISOString()
```

__�������� "��������� �����" - ���������� �����������, ��������� � Unix-�������__
`future.getTime()`
`Date(��������� �����)` \\ ����������� � ���� ��������� �����
`Date.now()` \\ �������� ��������� ����� ����������� �������

__���������� ��������� �������__
������ get - setAttribute

__������� ������ �������:__
```
const date = new Date();
var hour = date.getHours();
function timeFunction(hour){
  return hour >= 12 || hour <= 6 ? "������ ����!" : "������ �����!";
};
const time = timeFunction() + ". ������� �����: " + hour + ":";  // const time = `${timeFunction()}. ������� �����: ${hour}.`
console.log(time);

function timeFunction() {
    Data = new Date()
    hour = Data.getHours()
    nowIs = ""
    if (hour >= 12 || hour <= 6)
    {
        nowIs = "������ ����!";
        Time = nowIs + ". ������� �����: " + hour + ":";
        return Time;
    }
    else
    {
        nowIs = "������ �����!";
        Time = nowIs + ". ������� �����: " + hour + ":";
        return Time;
    }
}
console.log(timeFunction());
```
***
#### Internationalization - ��������� ������������� ���� � ����� � ����������� �� �����
***
```
new Intl.DateTimeFormat(��������� ������ ���� 'en-US').format('����\����������')
```
����� ��������� ����� ����� ������������ ������, ������� � ������ ������� ����� ������� � ���������. ����������
```
const options = 
{
    hour: 'numeric',
    minute: 'numeric',
    day: 'numeric',
    month: 'long'
}
new Intl.DateTimeFormat( 'en-US', options).format('����\����������')
```

����� �������� ������������ ���� �� �������� �������������
`const local = navigator.language`

�������������� ������������� ����� - ���������� API ��� �������������� ����� ��� ������ ������������ ������
```
const num = 3264746,44
new Intl.NumberFormat('en-US').format(num)
```
����� ����� ���� �������� ����� ���������� options 
__������� ��� �������������� �����__
```
const formatCur = function (value, locale, currency)
{
    return new Intl.NumberFormat (locale, 
    {
        style: 'currency',
        currency: 'currency',
    }.format(value)
}
```
***
#### setTimeout \ setInterval
***
__1. setTimeout__ : ������������� ���������� �������, ����� �������� ����� ��������� �������

������, ������� ��������� ���������� �������� ��� �������� ���������� ����.
`setTimeout((��������1, ��������2) => console.log('������� ��������')`, ����� � ������������� (1000 ����� = 1 ���) ����� �������� ������� ����� �������, ��������1 ��� ���������1, ��������2 ��� ���������2)

`setTimeout((ing1, ing2) => console.log('������� ��������, ���� ����������� ${ing1} � ${ing2}'), 3000, 'olives', 'spinach')`

���� ����� �� ������������� ���������� ����, ����� ���� �������

����� ���������� ���������� ������ �� ����, ��� �������� ����� �������� (�������� �������)
```
const ingridients = ['olives', 'spinach']
const pizzaTimer = setTimeout((ing1, ing2) => console.log('��� �����, ���� ����������� ${ing1} � ${ing2}'), 3000, ...ingridients) \\����� ��������, �� �� �����, ��� ingridients[0], ingridients[1]

if (ingridients.includes('spinach')) clearTimeout(pizzaTimer)
```
__2. SetInterval__ : ������������� ����� ����� ������� ������� ����� ���������� 
```
setInterval(function ()
{
    const now = new Date()
    console.log(now)
}, 1000)

(�������� ��� � ����� � �������� ������ �������)
```

