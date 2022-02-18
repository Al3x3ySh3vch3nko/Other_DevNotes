***
## DATES \ TIMES
***

moments.js - библиотека для времени

__Простой конструктор времени__
let now = new Date()

__Загружать данные в конструктор для их переформатировавния__
```
new Date ('December 24, 2015') 
new Date (2037, 10, 19, 15, 23, 56) \\ преобразует данные в формат даты и времени. В JS число месяца начинается с 0!
```

__Получить точку отсчета Unix-времени__
new Date (0) \\ 1 января 1070 г.
new Date (3 * 24 * 60 * 60 * 1000)  \\ добавить 3 дня к Unix-времени( в миллисекундах) 

__Получить год \ месяц \ день \ день недели \ часы \ минуты \ секунды__
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

__Получить данные в формате ISO__
```
future.toISOString()
```

__Получить "временной штамп" - количество миллисекунд, прошедшее с Unix-времени__
`future.getTime()`
`Date(временной штамп)` \\ преобразует в дату временной штамп
`Date.now()` \\ получить временной штамп конкретного момента

__Установить параметры времени__
вместо get - setAttribute

__Функции выбора времени:__
```
const date = new Date();
var hour = date.getHours();
function timeFunction(hour){
  return hour >= 12 || hour <= 6 ? "Доброе утро!" : "Добрый вечер!";
};
const time = timeFunction() + ". Текущее время: " + hour + ":";  // const time = `${timeFunction()}. Текущее время: ${hour}.`
console.log(time);

function timeFunction() {
    Data = new Date()
    hour = Data.getHours()
    nowIs = ""
    if (hour >= 12 || hour <= 6)
    {
        nowIs = "Доброе утро!";
        Time = nowIs + ". Текущее время: " + hour + ":";
        return Time;
    }
    else
    {
        nowIs = "Добрый вечер!";
        Time = nowIs + ". Текущее время: " + hour + ":";
        return Time;
    }
}
console.log(timeFunction());
```
***
#### Internationalization - позволяет форматировать дату и время в зависимости от языка
***
```
new Intl.DateTimeFormat(локальная строка типа 'en-US').format('дата\переменная')
```
Чтобы настроить метод нужно использовать объект, который в данном примере будет вынесен в отдельную. переменную
```
const options = 
{
    hour: 'numeric',
    minute: 'numeric',
    day: 'numeric',
    month: 'long'
}
new Intl.DateTimeFormat( 'en-US', options).format('дата\переменная')
```

Чтобы получить используемый язык из браузера автоматически
`const local = navigator.language`

Интернализация представления чисел - использует API для форматирования чисел под формат определенной страны
```
const num = 3264746,44
new Intl.NumberFormat('en-US').format(num)
```
Также может быть настроен через переменную options 
__Функция для форматирования чисел__
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
__1. setTimeout__ : устанавливает количество времени, после которого будет выполнена функция

Методы, которые позволяют установить интервал или отложить выполнение кода.
`setTimeout((параметр1, параметр2) => console.log('Функция запущена')`, время в миллисекундах (1000 млсек = 1 сек) после которого функция будет вызвана, аргумент1 для параметра1, аргумент2 для параметра2)

`setTimeout((ing1, ing2) => console.log('Функция запущена, наши ингредиенты ${ing1} и ${ing2}'), 3000, 'olives', 'spinach')`

Этот метод не останавливает выполнение кода, после этой функции

Чтобы прекратить выполнение метода до того, как заданное время подойдет (очистить счетчик)
```
const ingridients = ['olives', 'spinach']
const pizzaTimer = setTimeout((ing1, ing2) => console.log('Это пицца, наши ингредиенты ${ing1} и ${ing2}'), 3000, ...ingridients) \\спрэд оператор, то же самое, что ingridients[0], ingridients[1]

if (ingridients.includes('spinach')) clearTimeout(pizzaTimer)
```
__2. SetInterval__ : устанавливает время через которое функция будет вызываться 
```
setInterval(function ()
{
    const now = new Date()
    console.log(now)
}, 1000)

(вызывает лог с датой и временем каждую секунду)
```

