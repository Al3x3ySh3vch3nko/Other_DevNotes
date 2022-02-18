
********
JQuery
********

Google CDN. Ставится выше ссылки на файл JS.

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

Синтаксис:

$
=
jQuery();

Если ссылки добавлены в head:
$(document).ready(function()
{
$('h1').css('color', 'red');
});

Или просто добавлять их в конец body.

Пример синтаксиса:
* Вместо document.querySelector("h1");

Можно писать $('h1');

*Вместо document.querySelectorAll("button");    
    
Можно писать $("button"); 

* Для манипуляций со стилями следует писать 
$('селектор').css("color", "green");

* Для выбора значения в консоли:
console.log($("h1").css("font-size");

* Для добавления нового класса:
$("h1").addClass("big-title");

* Для добавления двух новых классов:
$("h1").addClass("big-title margin-50");

* Удаление класса:
$("h1").removeClass("big-title");

* Проверить в консоли имеет ли объект класс.
$("h1").hasClass("margin-50");

* Замена новым текстом:
$("h1").text("Bye");

* Замена новым текстом с разметкой:
$("button").html("<em>Bye</em>");

********
Манипуляции с атрибутами
********

* Узнать атрибут из консоли
console.log($("img").attr("src"));

$("a").attr("href", "https://www.yahoo.com");

* Узнать класс из консоли
$("h1").attr("class");

********
Обработчик событий
********

$("h1").click(function() 
{
    $("h1").css("color", "purple");
});


Вместо JS: 
for (var i = 0; i < 5; i++)
{
document.querySelectorAll("button")[i].addEventListener("click", function()
    {
        document.querySelector("h1").style.color = "purple";
    });
}

Можно писать:

$("button").click(function()
{
    $("h1").css("color", "purple");
});

* Добавление ивента при нажатии клавиши

$("body").keypress(function(event)
{
    console.log(event.key);
});

* Замена текста на странице клавишами
$("body").keypress(function(event)
{
    $("h1").text(event.key);
});

* Добавление события по действию мышки
$(h1).on("mouseover", function()
{
    $("h1").css("color", "purple");
});

$(h1).on("click", function()
{
    $("h1").css("color", "purple");
});

* Добавление элементов

До и после тэга h1

$("h1").before("<button>New</button>");
$("h1").after("<button>New</button>");

До и после контента внутри тэга h1

$("h1").prepend("<button>New</button>");
$("h1").append("<button>New</button>");

* Удаление элементов

* Быстро:

$("button").remove();
$("h1").gide();
$("h1").show();
$("h1").toggle();

* Плавно:

$("h1").fadeOut();
$("h1").fadeIn();
$("h1").fadeToggle();

* Cлайдом:

$("h1").slideUp();
$("h1").slideDown();
$("h1").slideToggle();

* Анимация:

$("h1").animate({opacity: 0.5});

* Объединение:
$("h1").slideUp().slideDown().animate({opacity: 0.5});

*******
Счетчик
*******

* Вариант с for.
for(var i=0; i<posts.length; i++)
{ 
    console.log(posts[i].title);
}; 

ИЛИ 

* Вариант с forEach

posts.forEach(function(post){console.log(post.title)});

*******
Уменьшение вводимых букв
*******

* используется библиотека lodash

Пример

const requestedTitle = _.lowerCase(req.params.test);

ИЛИ

const storedTitle = _.lowerCase(post.title);


