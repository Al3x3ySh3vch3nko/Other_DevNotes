***
## NODE JS
***

// ******* Определение переменных
```
const express = require("express");
const bodyParser = require("body-parser");
const ejs = require("ejs");
const mongoose = require("mongoose");
```
// ******* Технический код модулей
const app = express();
app.set('view engine', 'ejs');
app.use(bodyParser.urlencoded({extended: true}));
app.use(express.static("public"));

// ******* DB 
// Соединение
mongoose.connect("mongodb://localhost:27017/wikiDB", { useNewUrlParser: true, useUnifiedTopology: true });
// DB Схема
const postSchema = 
{
    title: String,
    content: String
};
// DB Модель
const Post = mongoose.model("Post", postSchema);

// ******* Контроль запуска сервера
app.listen(3000, function() {
    console.log("Server started on port 3000");
});

`$ node`
запуск файла через node
`node index.js`

***
#### REPL
***

Можно писать код, но будет отображаться как в консоли. 
Зайти в него через команду node
Появится скобка >, значит, в нем.

> con

Выдает возможные на текущий момент команды

> console.

Все возможности этой команды

> .exit
Выйти

или 
***
ctrl + c
***

> clear 
Очистить консоль

* Получение доступа к локальным файлам на компьютере

const fs = require('fs');
где fs это константа, далее - разрешение на на подключение модуля и название самого модуля.

Для отключения предупреждения в редакторе перед этим кодом добавить комментарий

//jshint esversion:6

*******
#### Файловая архитектура проекта под NodeJS
*******
```
Project Directoty
|
|node_modules
|+public 
||styles.css
|+views
|| +partials
|| |footer
|| |header
||about, home, contact, ect.
|app.js
|package.json
|package-lock.json 
```
*******
#### NPM:
*******

Создание основы

`npm init`
Запуск npm

Далее указать опционально имя пакета, версию, описание. Entry point - указание на основной файл JS, тестовую команду, репозиторий ГИТ, и пр.

Далее - согласиться.

Создается файл - package.json
(описание файла npm)

***
Установка пакетов
***

* Зайти в нужную директорию с npm init;
* npm install имя модуля c сайта 
 (npm install superherous);
* В json будет добавлена зависимость;
* В index.js можно удалить внутренний код node и использовать код из описания установщика, 
который позволяет работать модулю.
К примеру, 
var superherous = require("superherous");

***
## Node Express
***

Установка
* Выполнить указанные выше действия 

$ `mkdir myapp`
$ `cd myapp`
$ `npm init`

* Указывать при инициализации npm entry point: (index.js) или другой основной файл js в этой директории

* далее `$ npm install express`

* В `index.js` дать разрешение:

const express = require("express");

* Создать переменную

`const app = express();`

* Сделать функцию для портов

`app.listen(3000);`

или для отображения в консоли
```
app.listen(3000, function() 
{
console.log('Server started on port 3000');
});
```
* Проверить в консоли:

`node index.js`

* Для установки запроса и ответа GET

выше кода app.listen...
```
добавить код app.get("/", function (request, response) 
{

}
);
```
где `/` это домашняя страница

вместо `(request, response) может быть (req, res)`

Пример
```
app.get("/", function(req, res) 
{
res.send('Hello World');
});
```
Для отправки файла, такого как html следует использовать метод 
sendFile

Пример:
```
app.get("/", function(req, res) 
{
res.sendFile(index.html);
});
```
Для загрузки файла в релиз пути к файлу не будет, поэтому вместе с index.html следует использовать 
переменную `__dirname`
```
app.get("/", function(req, res) 
{
res.sendFile(__dirname + "index.html");
}); 
```
***
#### Nodemon - автоматически перезагружает сервер при измененях
***

* Установка

$ `npm install -g nodemon`

* В необходимой директории запустить
$ `nodemon index.js`

***
#### Отправка данных из формы
***

* Код HTML должен быть следующий
```
(1)
<form action="index.html" method="post">
    <input type="text" name="num1" placeholder="First number">
    <input type="text" name="num2" placeholder="Second number">
    <button type="submit" name="submit">Calculate</button>
</form>
```
ИЛИ
```
(2)
<form action="/" method="post">
    <input type="text" name="newItem">
    <button type="submit" name="submit">Add</button>
</form>
```
ИЛИ
```
(3)
<form action="/" method="post">
    <input type="text" action="compose.ejs" name="postTitle">
    <button type="submit" name="submit"> Publish </button>
</form>
```
***
* В index.js добавляется метод post
```
app.post("/", function(req, res)
{

}
);
```
* Устанавливается node модуль bodyparser
$ `npm install body-parser`

* В index.js устанавливаем разрешение на него
`const bodyParser = require("body-parser");`

* Устанавливается переменная 
`app.use(bodyParser.urlencoded({extended: true}));`

После этого будет возможно использовать метод req.body

Для созданной формы пример.
```
(1)
app.post("/", function(req, res)
{
var num1 = Number(req.body.num1);
var num2 = Number(req.body.num2);

var result = num1 + num2;

res.send(result);
});
```
ИЛИ
```
(2)
app.post("/", function(req, res)
{
var item = req.body.newItem;
console.log(item)
});
```
ИЛИ
```
(3)
app.post("/", function(req, res)
{
var composeInput = req.body.postTitle;
res.send(composeInput);
console.log(composeInput);
});
```
*******
#### Шаблон для express и body-parser
*******
```
const express = require("express");
const bodyParser = require("body-parser");

const app = express();

app.get("/", function(req, res)
{
res.send("Hello");
});

app.listen(3000, function()
{
console.log("Server started on port 3000");
});
```
*******
#### Шаблон для отправки html в зависимости от дня недели  
*******
```
const express = require("express");
const bodyParser = require("body-parser");

const app = express();

app.get("/", function(req, res)
{
var today = new Date();
var currentDay = today.getDay();

if (currentDay === 6 || currentDay === 0)
{
    res.sendFile(__dirname + "/weekend.html");
}
else
{
    res.sendFile(__dirname + "/weekend.html");
}
});

app.listen(3000, function()
{
console.log("Server started on port 3000");
});
```
*******
## EJS
*******

$ `npm i ejs`

* Добавить код `app.use("view engine", "ejs")`;
после констант и после константы express

* Создается новая директория `views` в папке проекта

* В ней создается файл `list.ejs` или другой основной

* В нем помещается весь html код

* Для html кода используется маркер `<%= %>`

* Вместо res.send используется метод `res.render`

*** 
Пример
```
app.get("/", function(req, res)
{
var today = new Date();
var currentDay = today.getDay();
var day ="";
```
// Рабочий или нерабочий день
// ******************************************************************************
```
// if (currentDay === 6 || currentDay === 0)
// {
    //     day = "Weekend";
    //     res.render("list",{kindOfDay: day});
    // }
    // else
    // {
//     day = "Weekday";
//     res.render("list",{kindOfDay: day});
// }
// ******************************************************************************
```

// День недели if-else
// ******************************************************************************
```
// if (currentDay === 0)
// {
    //     day = "ВСКР.";
    // }
    // if else (currentDay === 1)
    // {
        //     day = "ПН.";
        // }
        // if else (currentDay === 2)
        // {
            //     day = "ВТ.";
            // }
            // if else (currentDay === 3)
// {
//     day = "СР.";
// }
// if else (currentDay === 4)
// {
//     day = "ЧТ.";
// }
// if else (currentDay === 5)
// {
//     day = "ПТ.";
// }
// if else (currentDay === 6)
// {
//     day = "СБ.";
// }
// ******************************************************************************
```
```
switch (currentDay)
{
    case 0:
    day = "ВСКР.";
    break;
    
    case 1:
    day = "ПН.";
    break;

    case 2:
    day = "ВТ.";
    break;

    case 3:
    day = "СР.";
    break;

    case 4:
    day = "ЧТ.";
    break;

    case 5:
    day = "ПТ.";
    break;

    case 6:
    day = "СБ.";
    break;

    console.log("Error: current day is equal to: " + currentDay);
}

res.render("list",{kindOfDay: day});

});
```
* Для включения JS в HTML следует использовать `<% %>`

* Для включения других статичный файлов в express следует создать папку public, которая будет отслеживаться express

* В app.js следует добавить код отслеживания
`app.use(express.static("public"));`

***
Имплементация блоков из разных файлов через EJS (layout)
***

* Создается соответствующий файл 
footer.ejs или header.ejs

* В них помещается код, включая открывающийся body в хэдере и закрывающийся body в футере.

* Для включения кода добавляется код в list.ejs 
<%- include("header") -%>  
<%- include("footer") -%> 

***
Создание модулей
***

* Создается отдельный файл с функцией

* в app.js создается новое разрешение с названием файла, к примеру.

const date = require(__dirname + "date.js");    

* В новом файле создается код экспорта функции. 

К примеру

module.exports = getDate;

function getDate(){

let today = new Date();

let options = 
{
    weekday: "long",
    day: "numeric",
    month: "long"
};

let day = today.toLocaleDateString("en-US", options);

return day;
};

* Вместо module.exports можно использовать exports. 

* Для вызова функции в дальнейшем ее надо писать со скобками

к примеру

let day = getDate();

* Для уточнения экспортируемой функции, чтобы возможно было вызвать несколько функций можно писать

module.exports.getDate = getDate;
и вторую
module.exports.getDay = getDay;

и так далее.

* В app.js после этого можно вызывать 

    let day = date.getDate();

    или
    
    let day = date.getDay();
    
*******
Часто используемые модули   
*******

* util для вывода конкретной функции в консоли. К примеру, функция с названием obj

console.log(util.inspect(obj);

* console 

console.log - общий поток

console.error - поток ошибок

* EventEmmiter

var EventEmmiter = require("events").EventEmitter;
