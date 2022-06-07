********
## DOM - API интерфейс, который позволяет движку JS взаимодействовать с html

DOM состоит из нод (объекты), которые имеют разный тип. Каждый тип может иметь свои методы.

Типы нод:
"1 уровень"
- EventListener
"2 уровень"
- Node
- Window
"3 уровень" - дочерние для типа Node:
- элементы (html элементы)
- текст
- комментарий
- документ (содержит набиболее часто встречающиеся методы при работе - селекторы и пр.)

DOM работает по принципу наследование. То есть, дочерний элементы имеют доступ к методам родительских нод
********
***
__Выбор элементов. Просмотр DOM элементов через консоль__
***
```
console.log(document.documentElement) // все
console.log(document.head) // элемент head
console.log(document.body) // элемент body
```
Некоторые методы такие как getElementByTagName \ ByClassName возвращают не псевдомассив \ node list, а life collection. То есть, коллекцию элементов, которая автоматически обновляется

* Как открыть структуру всего документа.
`document;`   

* Выбор первого дочернего элемента
`document.firstElementChild;`

* Выбор первого дочернего для первого дочернего.
`document.firstElementChild.document.firstElementChild`

* Выбор последнего дочернего элемента.
`document.lastElementChild`

* Сохранение выбранного селектором элемента в переменной
(пример)
`var heading = document.firstElementChild.document.firstElementChild`
и манипуляция им
`heading.innerHTML = "Good Bye";`
`heading.style.color = "red";`

* Выбор типа тэга(объекта)
`document.querySelector("input").click();`

* Выбор по типу тэга
`document.getElementsByTagName("li");`
Нельзя установить параметры для элементов в виде
`document.getElementByTagName("li").style.color ="purple";`
потому, что это всевдонабор элементов в СТРОКЕ. Для выбора конкретного элемента нужно указывать место в массиве:
`document.getElementByTagName("li")[2].style.color ="purple";`
`const allButtons = document.getElementByTagName (button)`
`console.log(allButtons` // покажет все елементы с тегом button

* Выбор по классу
`document.getElementsByClassName("btn");`
не сработает:
`document.getElementsByClassName("btn").style.color = "red";`
Нужно
`document.getElementsByClassName("btn")[0].style.color = "red";`

* Выбор по ID
`document.getElementById("btn");`
cработает, так как это НЕ строка, а единичный объект:
`document.getElementById("btn").innerHTML = "Good Bye";`

* Выбор по селектору ОДНОГО объекта, удовлетворяющего параметрам.
`document.querySelector("h1");`
`document.querySelector("#title");`
`document.querySelector(".btn");`

* Комбинации:
`document.querySelector("li a");`
`document.querySelector("li.title");` (если класс в тэге как дочерний)
`document.querySelector("li .title");` (если класс в тэге как более далекий потомок)

* Выбор по селектору ВСЕХ объектов, удовлетворяющих параметрам.
`document.querySelectorAll("li a");` 
* Манипуляции происходят по индексу.
`document.querySelectorAll("li a")[2].style.color = "blue";`
***
__Прохождение DOM__
***
`const h1 = document.querySelector('h1')`;
выбор элемента h1

* Going downwards: child
`console.log(h1.querySelectorAll('.highlight'));` // выбор всех элементов с классом в элементе h1
`console.log(h1.childNodes);` // список нод-элементов
`console.log(h1.children);` // список дочерних элементов (не включены все нод-элементы) - дает html коллекцию
`h1.firstElementChild.style.color = 'white';` // первый дочерний элемент
`h1.lastElementChild.style.color = 'orangered';` // последний дочерний элемент

* Going upwards: parents
`console.log(h1.parentNode);` // выбор родительского нод-элемента
`console.log(h1.parentElement);` // выбор родительского html-элемента
`h1.closest('.header').style.background = 'var(--gradient-secondary)';`
`h1.closest('h1').style.background = 'var(--gradient-primary)';`
// метод, выбирающий родительский элемент независимо от его положения в DOM

* Going sideways: siblings
`console.log(h1.previousElementSibling);`
`console.log(h1.nextElementSibling);`
`console.log(h1.previousSibling);`
`console.log(h1.nextSibling);`
```
console.log(h1.parentElement.children);
[...h1.parentElement.children].forEach(function (el) {
  if (el !== h1) el.style.transform = 'scale(0.5)';
});
```

* Узнать лист примененных к объекту классов (в консоли)
`.classList;`
Пример:
`document.querySelector("button").classList;`

* Добавить класс к листу:
`document.querySelector("button").classList.add("invisible");`

* Перезаписать класс у листа:
`document.querySelector("button").className = 'form-control error'`

* Удалить класс из листа:
`document.querySelector("button").classList.remove("invisible");`

* Переключатель:
`document.querySelector("button").classList.toggle("invisible");`

* Замена текста:
с вложенными тегами:
`document.getElementById("title").innerHTML = "Good Bye";`
только текст:
`document.getElementById("title").textContent = "Good Bye";`
    
* Выбор по атрибутам:
`document.querySelector("a");`
далее
`document.querySelector("a").attributes;`
будет список атрибутов и можно выбрать необходимый атрибут:
`document.querySelector("a").getAttribute("href");`
Установить новый атрибут:
`document.querySelector("a").setAttribute("href", "http:....");`

***
__Манипуляции с элементами__
***
__Создание элементов__ 
* см метод insertAdjacentHTML (примеры в bankist app)
* document.createElement('div')

Пример добавления блока с оповещением о cookie
`const header = document.querySelector('.header')`
// выбор элемента в котором будет отображаться сообщение
`const cookiesMessage = document.createElement('div')`
// создание нового div где будет записано сообщение
`cookiesMessage.classList.add('cookie-message')`
// добавление к этому новому div класса со стилями из css
`message.innerHTML = 'We use cookies for improve functionality and analytics. '<button class="btn btn--close-cookie"> Ok! </button>'`
// добавление текста и разметки в div
`header.prepend('message')`
или
`header.append('message')`
// вызов функции для вывода сообщения cookies. метод prepend добавляет элемент как первый дочерний элемент, append - как последний 

Для добавления копии элемента 
`header.prepend('message')`
`header.append('message.cloneNode(true)')`

* помещение элемента до \ после 
`header.before('message')`
`header.after('message')`

* удаление элементов
`document.qerySelector('.btn--close-cookie')`
`addEventListener('click', function()`
`{`
    `message.remove()`
`})`

__Добавление стилей к элементам__
`message.style.backgroundColor = '#37383d'`
`message.style.width = '120%'`
\\ вместо message можно использовать выбранный элемент

Нельзя этими способами получить доступ к стилям, которые заданы инлайн

Для их получения требуется использовать метод 
`getComputedStyle(message).color` \\ вместо color - необходимый параметр

Чтобы добавить значение к существующему через js
`message.style.height = Number.parseFloat(getComputedStyle(message).height, 10) + 40 + 'px'`

* Для изменения стилей из css: root (в js это эквивалент document)
`document.documentElement.style.setProperty('--color-primary', 'oranged')`
\\ меняется значение --color-primary из :root сss на новое

* для получения доступа к атрибутам (стандартные атрибуты)
`const logo = document.querySelector('.nav__logo')`
`console.log(logo.alt)`
`console.log(logo.src)` \\ дает итоговый путь - абсолютный
`console.getAttribute('src')` \\ дает путь как он был прописан в коде - может быть относительным 

`console.log(logo.className)`

для получения доступа к нестандартным атрибутам 
`logo.getAttribute('designer')`
для установления атрибута
`logo.getAttribute('company', 'bankist')` \\ первый параметр это название атрибутв, второй - его значение

для добавления атрибута
`logo.alt('Это лого')` \\ вместо alt требуется указывать нужный атрибут 

для получения атрибутов с названием 'data-' (пример: <img data-version-number = '3.0') требуется использовать отдельный метод

`console.log(logo.dataset.versionNumber)`

__ Методы работы с классами__
`logo.classList.add('класс1', 'класс2')`
`logo.classList.remove('класс1', 'класс2')`
`logo.classList.toggle('класс1', 'класс2')`
`logo.classList.contains('класс1', 'класс2')`

__Получение значения html__
`console.log(document.querySelector('идентификатор').textContent`
выводит html содержание "объекта"

__Получение значений из input__
для получения и установления значения из поля input или в поле input требуется использовать value

ПРИМЕР:
получение - `console.log(document.querySelector('идентификатор поля input').value)`
установить значение - `document.querySelector('идентификатор поля input').value = значение` `document.querySelector('идентификатор').addEventListener('тип ивента', функция-handler)`

***
#### EventsListener:
***

__Event__ - это сигнал, который генерируется из конкретного DOM узла при каком-то событии с этим узлом. сигнал будет генерироваться всегда самостосятельно даже если нет EventsListener на него.
__В листенер можно передать только 1 аргумент, и это - ивент. Для передачи других нужно использовать this или передавать их через объект или массив__
`event.target` - элемент, на котором изначально сработал ивент
`event.currentTarget` - элемент, на котором срабатывает ивент в настоящий момент (то же самое что и this в Листенерах)

Стадии:
__1) capturing__ - при событии event "сигнал" генерируется в document и доходит через родительские элементы элемента, в связи с которым произошло событие, не в самом элементе

__2) targeting__ - при наличии сигнала движок далее ожидает функцию-колбэк

__3) bubbling__ - при срабатывании Листенера event через родительские элементы возвращается обратно в объект document

__Cпособы создания eventListener__ 
__1.__ более новый (позволяет добавлять несколько листенеров к одному элементу, позволяет убрать листенер если он более не нужен)
```
const h1 = document.querySelector('h1')
h1.addEventListener('mouseenter', function(event) 
{
    alert ('hello')
}
```
__2.__ более старый (при добавлении второго листенера к элементу он перепишет первый, не позволяет убрать листенер если он более не нужен)
```
h1.onmouseenter = function(event) 
{
    alert ('hello')
}
```
__3.__ в разметке HTML (не используется)
`<h1 onclick = 'alert' ('HTML alert')>`
__4.__ создание eventListener через делегирование (передача созданного по варианту 1 листенера родительского элемента дочерним элементам - лучший способ так как позволяет задать листенер не существующим еще (в проессе загрузки) элементам)

__Стадии работы__
- добавление листенера к текущему родительскому элементу 
- определить на каком элементе должен сработать eventListener (через event.target)

__Удаление Листенера (только для способа № 1)__
```
const h1 = document.querySelector('h1')
const alertH1 = function(event) 
{
    alert ('hello')
    h1.removeEventListener('mouseenter', alertH1)
}

h1.addEventListener('mouseenter', alertH1)
```
удалить через некоторое время
```
setTimeout(() =>h1.removeEventListener('mouseenter', alertH1), 3000)
```

__Удаление bubbling или capturing__

`event.stopPropagation()`
 
_В логике приложения если значение не установлено можно использовать следующий код_ 

`if (!guess) {код}`

в данном случае если значение элемента - в данном случае переменной guess равно нулю то устанавливается значение falses (0 это неистинное значение)
ПРИМЕР:
```
if (!guess)
{
    document.querySelector(.message).textContent = 'No Number'
}
```
ПРИМЕР:
Cоздание функции по клику на все кнопки с классом drum (7 штук)
```
    let drumNumber = document.querySelectorAll('.drum').length;

for (i=0; i<drumNumber; i++)
{
    document.querySelectorAll('.drum')[i].addEventListener('click', f_listenerClick)
}

function f_listenerClick()
{
    alert('@#$')
}
```

Для отслеживания нажатия кнопок следует создать "глобальный" EventsListener
```
document.addEventListener('keydown', function(event)
{
    console.log(event)
})
```

Для спецификации кнопки : 
```
console.log(event.key)
```
Для реагирования на нажатие кнопки:
```
document.addEventListener('keydown', function(event)
{
    if(event.key === 'Escape')
    {
        
    }
})
```
Для того, чтобы определить какой класс в данный момент присвоен/ не присовен элементу
```
document.addEventListener('keydown', function(event)
{
    if(event.key === 'Escape')
    {
        if(modal.classList..contains('hidden'))
        {
            
        }
        if(!modal.classList..contains('hidden'))
        {
            
        }
    }
})
```
или 
```
document.addEventListener('keydown', function(event)
{
    if(event.key === 'Escape' && !modal.classList.contains('hidden'))
    {
    f_closeModal()
    }
})
```
Первый и второй код идентичны.
```
//Var1
document.querySelector("button").addEventListener("click", handleClick)
function handleClick()
{
alert("I got clicked");
}
```
```
//Var2
document.querySelector("button").addEventListener("click", function(){alert('I got clicked.');});
```

__Добавление события нажатия кнопки клавиатуры для ВебКнопки__
```
var numbersOfDrumButtons = document.querySelectorAll(".drum").length;
for (var i = 0; i < numbersOfDrumButtons; i++) 
    {
    document.querySelectorAll(".drum")[i].addEventListener("click", function()
        {
        alert("i got clicked");
        });
    }
```

___Еще пример анонимной функции:___

Это тоже самое,
```
$0.addEventListener("click", function()
{
    console.log("I got clicked");
}
); 
```
что
```
$0.addEventListener("click", respondToClick);

function respondToCLick()
{
    console.log("I got clicked");
}
```

__Пример калькулятора:__
```
function add(num1, num2)
{
    return num1 + num2;
}

function subtract(num1, num2)
{
    return num1 - num2;
}

function multiply(num1, num2)
{
    return num1 * num2;
}

function divide(num1, num2)
{
    return num1 / num2;
}

function calculator(num1, num2, operator)
{
    return operator(num1, num2);
}
```
Вызов:
`calculator(4, 5, имя функции)`;
