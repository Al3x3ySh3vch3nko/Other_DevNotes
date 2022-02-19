Генераторы шаблонов CSS
- grid.layoutit.com
- csslayout.io
- griddy.io
- purecss.io
- cssgrid-generator.netlify.app
- loading.io
- cssgrid.id
- cssflex-generator.netlify.app

1) Шаблон для нормализации:
*, 
::before,
::after {
    box-sizing: border-box;
}

2) Или более гибкий враиант + иные нормализаторы:
===
:root {
    box-sizing: border-box;
    font-size: calc(0.5em + 1vh);
    margin: 0;
    padding: 0;
}

*,
    ::before,
    ::after {
    box-sizing: inherit;
}

html {
 scroll-behavior: smooth;
}
===

---------------------------------------------------------------------------------------------
Для адаптирования размера шрифта под размер вьюпорта делать расчеты по 
https://habr.com/ru/post/310186/
и 
https://m.habr.com/ru/company/mailru/blog/315196/

HTML
<p class="fluid-font-size">This text is responsive to your browser width. Just resize it!</p>

CSS
@function strip-unit($number) {
  @if type-of($number) == 'number' and not unitless($number) {
    @return $number / ($number * 0 + 1);
  }

  @return $number;
}

@function calcFluidFontSize($f-min, $f-max, $w-min, $w-max, $units: px) {
  $f-min: strip-unit($f-min);
  $f-max: strip-unit($f-max);
  $w-min: strip-unit($w-min);
  $w-max: strip-unit($w-max);
  
	$k: ($f-max - $f-min)/($w-max - $w-min);
	$b: $f-min - $k * $w-min;

	$b: $b + $units;

	@return calc( #{$k} * 100vw + #{$b} );
}

@mixin fluidFontSize($f-min, $f-max, $w-min, $w-max, $fallback: false) {
  
  font-size: $f-min;
  
  @media (min-width: $w-min) {
    @if ($fallback) {
      font-size: $fallback;
    }
    font-size: calcFluidFontSize($f-min, $f-max, $w-min, $w-max, px);  
  }
  @media (min-width: $w-max) {
    font-size: $f-max;
  }
}

.fluid-font-size {
  @include fluidFontSize(16px, 24px, 480px, 1280px, 18px);
}
----------------------------------------------------------------------------------------------

Для задания конкретному блоку свойства content-box следует писать к примеру:

.third-party {
    box-sizing: content-box;
}

+ IE: при работе с тэгом main следует объявлять его как блочный 
main{
display: block;}

3) Применение межстрочного интервала ко всему документу

body{
line-height: 1.2; }
(без единиц измерения! - тогда он будует высчитывать пропорции автоматически
нужно, чтобы одныжды указать это и забыть)

4) Переменные:
:root {
--main-font: Helvetica; Arial; sans-serif;
}

p {
font-family: var(--main-font);
}

или для резервных значений - пишутся как вторые

p{
font-family: var(--main-font, sans-serif);
}

Переопределение переменной в конкретном контейнере:

.dark{
...
...
--main-bg: dark-blue;
--font-size:13px;
}

5) колонки равной высоты
__________________
.wrapper {
margin-left: -1.5em;
margin-right: -1.5em;
}

.container {
display: table;
width: 100%;
border-spacing: 1.5em 0;
}

.main{
display: table-cell;
width: 100%;
}

.sidebar{
display: table-cell;
width: 30%;
margin-left: 1.5em;
padding:1.5em;
}
____________

6) <details>
https://habr.com/ru/post/477520/

7) 

Распорка через псевдоэлемент для float:

.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

8) Львиная доля динамических эффектов, создаваемых с помощью CSS, опираются на несколько псевдоклассов, главный из которых, конечно же, :hover. Весь секрет заключается в сочетании контекстных селекторов и псевдоклассов. Посмотрите на пример:

li.top ul.submenu {
  display: none;
}

li.top:hover ul.submenu {
  display: block;
}

Первое правило прячет список-подменю. Второе правило гласит: «если на верхний пункт меню, в котором находится подменю, наведут курсор, то надо показать подменю». Вот так всё просто.

Общий принцип такой: родительский элемент реагирует на наведение мыши и изменяет свойства элементов-потомков. То есть всё работает на контекстных селекторах вида селектор1:hover селектор2.

9) Лайтбокс
https://morioh.com/p/7dda846a227e?f=5c21fb01c16e2556b555ab32

10) Библиотеки CSS
http://odinokun.com/2020-01-10-10-luchshih-bibliotek-dlya-css-animaci.html

11) принципы CSS
https://habr.com/ru/post/474360/

12) Сброс стилей CSS
/* Box sizing rules */
*,
*::before,
*::after 
{
    box-sizing: border-box;
}

/* Remove default padding */
ul[class],
ol[class] 
{
    padding: 0;
}

/* Remove default margin */
body,
h1,
h2,
h3,
h4,
p,
ul[class],
ol[class],
li,
figure,
figcaption,
blockquote,
dl,
dd 
{
    margin: 0;
}

/* Set core body defaults */
body 
{
    min-height: 100vh;
    scroll-behavior: smooth;
    text-rendering: optimizeSpeed;
    line-height: 1.5;
}

/* Remove list styles on ul, ol elements with a class attribute */
ul[class],
ol[class] 
{
    list-style: none;
}

/* A elements that don't have a class get default styles */
a:not([class]) 
{
    text-decoration-skip-ink: auto;
}

/* Make images easier to work with */
img 
{
    max-width: 100%;
    display: block;
}

/* Natural flow and rhythm in articles by default */
article > * + * 
{
    margin-top: 1em;
}

/* Inherit fonts for inputs and buttons */
input,
button,
textarea,
select 
{
    font: inherit;
}

13) Документы для разработки

https://devdocs.io/

14) ресурсы https://www.frontendmentor.io/

=======
EFFECTS
=======


Glitch EFFECTS

.glitchfy {
  position: relative;
  outline: 0;
  border: none;
}

.glitchfy::before {
  content: '';
  opacity: 0;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.glitchfy::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  box-shadow: rgba(116, 3, 3, 0.75) 0 0 15px 2px;
  background: #fd1717a2;
  height: 1px;
  opacity: 0;
}

.glitchfy:hover::before {
  opacity: 1;
}

.glitchfy:hover::after {
  -webkit-animation: scan 2s infinite;
  animation: scan 2s infinite;
  opacity: 1;
}

@-webkit-keyframes glitch {
  0% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
  }

  5% {
      -webkit-transform: skewX(2deg);
      transform: skewX(2deg);
      opacity: 0.75;
  }

  10% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  15% {
      -webkit-transform: skewX(-5deg);
      transform: skewX(-5deg);
      opacity: 0.75;
  }

  20% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  45% {
      -webkit-transform: skewX(3deg);
      transform: skewX(3deg);
      opacity: 0.75;
  }

  50% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  55% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 0.75;
  }

  60% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  75% {
      -webkit-transform: skewX(2deg);
      transform: skewX(2deg);
  }

  80% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
  }

  85% {
      -webkit-transform: skewX(-8deg);
      transform: skewX(-8deg);
      opacity: 0.75;
  }

  90% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  100% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
  }
}

@keyframes glitch {
  0% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
  }

  5% {
      -webkit-transform: skewX(2deg);
      transform: skewX(2deg);
      opacity: 0.75;
  }

  10% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  15% {
      -webkit-transform: skewX(-5deg);
      transform: skewX(-5deg);
      opacity: 0.75;
  }

  20% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  45% {
      -webkit-transform: skewX(3deg);
      transform: skewX(3deg);
      opacity: 0.75;
  }

  50% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  55% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 0.75;
  }

  60% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  75% {
      -webkit-transform: skewX(2deg);
      transform: skewX(2deg);
  }

  80% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
  }

  85% {
      -webkit-transform: skewX(-8deg);
      transform: skewX(-8deg);
      opacity: 0.75;
  }

  90% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
      opacity: 1;
  }

  100% {
      -webkit-transform: skewX(0deg);
      transform: skewX(0deg);
  }
}

@-webkit-keyframes scan {
  0% {
      top: 0%;
  }

  50% {
      top: 95%;
  }

  100% {
      top: 100%;
  }
}

@keyframes scan {
  0% {
      top: 0%;
  }

  50% {
      top: 95%;
  }

  100% {
      top: 100%;
  }
}

