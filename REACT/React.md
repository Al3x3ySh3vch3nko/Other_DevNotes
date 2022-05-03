Ссылка: [Стиль написания кода от AirBnb](https://github.com/leonidlebedev/javascript-airbnb/tree/master/react)
Ссылка: [React form hook](https://react-hook-form.com)
Ссылка: [react-router](https://reactrouter.com/)

> React разделяет ответственность с помощью слабо связанных единиц, называемых «компоненты», которые содержат и разметку, и логику - вместе.

> Использует JSX - расширение языка JavaScript. React можно использовать и без JSX.
JSX допускает использование любых корректных JavaScript-выражений внутри фигурных скобок
После компиляции каждое JSX-выражение становится обычным вызовом JavaScript-функции, результат которого — объект JavaScript.
Из этого следует, что JSX можно использовать внутри инструкций if и циклов for, присваивать переменным, передавать функции в качестве аргумента и возвращать из функции.

#### Babel компилирует JSX в вызовы React.createElement().
В результате получается подобный объект. Эти объекты называются React-элементами. 
React читает эти объекты и использует их, чтобы конструировать и поддерживать DOM. 
В отличие от DOM-элементов, элементы React — это простые объекты, не отнимающие много ресурсов. React DOM обновляет DOM, чтобы он соответствовал переданным React-элементам. 
Элементы — это то, «из чего сделаны» компоненты.
Элементы React иммутабельны.


```
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Привет, мир!'
  }
};
```

#### Рендеринг:
Обычно в приложениях, написанных полностью на React, есть только один корневой элемент. 
Для рендеринга React-элемента в корневой узел DOM - вызов ReactDOM.render() с React-элементом и корневым DOM-узлом в качестве аргументов:
```
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```
React DOM сравнивает элемент и его дочернее дерево с предыдущей версией и вносит в DOM только минимально необходимые изменения.


#### Импорт 
`var React = require('react');`
`var ReactDOM = require('react-dom');`
// устаревшее, можно 
`import React from 'react';`
`import ReactDOM from 'react-dom';`

`ReactDOM.render(<h1>Hello There</h1>, document.getElementById('root'));`
// параметры render 
// 1) что показывать, 
// 2) где показывать,
// 3) callback, то есть когда функция будет завершена

//это тоже самое что:
`var h1 = document.createElement('h1');`
`h1.innerHTML = 'HelloWorld';`
`document.getElementById('root').appendChild(h1);`

Связано с использованием JSX - расширение JS через встроенный Babel.

2 ---
//Для добавления нескольких элементов - обернуть в div 
```
ReactDOM.render(
<div>
<h1>Hello</h1>
<p>There</p>
</div>,
document.getElementById("root"));
```
3 ---
```
// Чтобы вводить в html, внутри JSX, код JS, нужно обернуть его в {}
// Пример
import React from "react";
import ReactDOM from "react-dom";

const name = "Alex";
const luckNumber = "8";
const smthElse = "12345";

ReactDOM.render(
  <div>
    <h1>Hello {name}!</h1>
    <p>Your lucker number is {luckNumber} {smthElse}</p>
  </div>,
  document.getElementById("root")
);
```
//Или через шаблонные литералы
```
ReactDOM.render(
  <div>
    <h1>Hello {name}!</h1>
    <p>Your lucker number is {{`${luckNumber} ${smthElse}`}</p>
  </div>,
  document.getElementById("root")
);
```
`<p>Your lucker number is {{`${luckNumber} ${smthElse}`}</p>`
// равняется
`<p>Your lucker number is {luckNumber + " " + smthElse}</p> `


>Пример
```
import React from "react";
import ReactDOM from "react-dom";

let name = "My Name";
var today = new Date();
var year = today.getFullYear();

ReactDOM.render
(
  <div>
    <p>Created by {name}.</p>
    <p>Copyright {year}.</p>
  </div>,
  document.getElementById("root")
);
```

5---
// Для того, чтобы дать задать тип ссылки в скрипте нужно 
`<script src="../src/index.js" type="text/JSX"></script>`

#### Добавление стилей 
```
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(
  <div>
    <h1 class="blue" contentEditable="true" spellCheck="false">
      My Favourite Foods
    </h1>
    <div>
      <img
        className="img"
        src="https://avatars.mds.yandex.net/get-pdb/1771637/74d3e432-323a-4b24-b410-7577ddc99726/s1200?webp=false"
      />
      <img
        className="img"
        src="https://avatars.mds.yandex.net/get-pdb/1771637/74d3e432-323a-4b24-b410-7577ddc99726/s1200?webp=false"
      />
      <img
        className="img"
        src="https://avatars.mds.yandex.net/get-pdb/1771637/74d3e432-323a-4b24-b410-7577ddc99726/s1200?webp=false"
      />
    </div>
  </div>,
  document.getElementById("root")
);
```
//и в сss в то же время
```
.img 
{
  width: 100px;
  height: 100px;
}
```

Добавление стилей онлайн

- с двойными фигурными скобками (!) так как параметр должен быть в виде JS объекта + сами фигурные скобки

```
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(<h1 style={{color:"red"}}>Hello World!</h1>, document.getElementById("root"));
```
- через переменную. В этом случае все параметры css переводятся в объект JS и в JSX пишется переменная
```
import React from "react";
import ReactDOM from "react-dom";

const customStyle = 
{
  color: "red",
  fontSize: "20px",
  border: "1px solid black"
}

ReactDOM.render(<h1 style={customStyle}>Hello World!</h1>,
document.getElementById("root"));
```

Для изменения параметров объекта можно изменять переменную как в JS

`customStyle.color = "blue";`

=======

//Show a single h1 that says "Good morning" if between midnight and 12PM.
//or "Good Afternoon" if between 12PM and 6PM.
//or "Good evening" if between 6PM and midnight.
//Apply the "heading" style in the styles.css
//Dynamically change the color of the h1 using inline css styles.
//Morning = red, Afternoon = green, Night = blue.
```
import React from "react";
import ReactDOM from "react-dom";

let Data = new Date();
let hour = Data.getHours();
let minutes = Data.getMinutes();
let nowIs; 
let Time = nowIs + " Текущее время: " + hour + ":" + minutes;
const Style = 
{
  color: "red",
}

// Render 

ReactDOM.render(
  <h1 style={Style} class="heading">{Time}</h1>,
  document.getElementById("root")
);

 // Определение времени суток, выбирая между утром, днем и вечером
function now()
```

//Show a single h1 that says "Good morning" if between midnight and 12PM.
//or "Good Afternoon" if between 12PM and 6PM.
//or "Good evening" if between 6PM and midnight.
//Apply the "heading" style in the styles.css
//Dynamically change the color of the h1 using inline css styles.
//Morning = red, Afternoon = green, Night = blue.
```
import React from "react";
import ReactDOM from "react-dom";
let Data = new Date();
let hour = Data.getHours();
let minutes = Data.getMinutes();
let Time = timeFunction() + " Текущее время: " + hour + ":" + minutes;
const customStyle = 
{
  color: "red",
}

if (hour >= 24 || hour <= 1) {
  customStyle.color = "purple";
} else {
  customStyle.color = "black";
  ;
}

// Render 
ReactDOM.render(
  <h1 className="heading" style={customStyle}>{Time}</h1>,
  document.getElementById("root")
);

 // Определение времени суток, выбирая между утром, днем и вечером
 function timeFunction(nowIs) {
   if (hour >= 24 || hour <= 1) {
      nowIs = "Доброе утро!";
      Time = nowIs;
      return Time;
      ;
  } else {
      nowIs = "Добрый вечер!";
      Time = nowIs;
      return Time;
      ;
  }
}
```
====== Более простой вариант
```
//Show a single h1 that says "Good morning" if between midnight and 12PM.
//or "Good Afternoon" if between 12PM and 6PM.
//or "Good evening" if between 6PM and midnight.
//Apply the "heading" style in the styles.css
//Dynamically change the color of the h1 using inline css styles.
//Morning = red, Afternoon = green, Night = blue.

import React from "react";
import ReactDOM from "react-dom";

let Data = new Date();
let hour = Data.getHours();

// ======= Блок выбора приветствия
let greeting; 

let customStyle = {
  color: ""
 };

if (hour < 12)
{
  greeting = "Доброе утро.";
  customStyle.color = "blue";
}
else if (hour < 18)
{
  greeting = "Добрый день.";
  customStyle.color = "green";
}
else 
{
  greeting = "Добрый вечер.";
  customStyle.color = "black";
}
// ======= Окончание блока Выбора приветствия

// ======= Render 
ReactDOM.render(
  <h1 className = "heading" style={customStyle}>{greeting}</h1>,
  document.getElementById("root")
);
```
#### Компоненты
Во многом компоненты ведут себя как обычные функции JavaScript. Они принимают произвольные входные данные (так называемые «пропсы») и возвращают React-элементы, описывающие, что мы хотим увидеть на экране.
Пишется функция, название которой в Паскаль-стиле и внутри они возвращает часть кода, который является компонентом. Если компонент начинается с маленькой буквы, React принимает его за DOM-тег. 

Проще всего объявить React-компонент как функцию:

```
function Welcome(props) {
  return <h1>Привет, {props.name}</h1>;
}
```

Эта функция — компонент, потому что она получает данные в одном объекте («пропсы») в качестве параметра и возвращает React-элемент. Такие компоненты называются «функциональными», так как они буквально являются функциями.

Ещё компоненты можно определять как классы ES6:
```
class Welcome extends React.Component {
  render() {
    return <h1>Привет, {this.props.name}</h1>;
  }
}
```
С точки зрения React, эти два компонента эквивалентны.

Пример использования компонента.
```
function Heading()
{
  return <h1>My Favourite Foods</h1>;
}
```
для того, чтобы использовать компонент его пишут в коде как тэг
```
<Heading></Heading>
```
но лучше
```
<Heading />
```

#### Пропсы

React-элементы, представляющие собой DOM-теги это просто "DOM компоненты":

>Компонент никогда не должен что-то записывать в свои пропсы — вне зависимости от того, функциональный он или классовый.
[ ! ] React-компоненты обязаны вести себя как чистые функции по отношению к своим пропсам. [ ! ] 

`const element = <div />;`

Но элементы могут описывать собственные компоненты:

`const element = <Welcome name="Алиса" />;`

> Когда React встречает подобный элемент, он собирает все JSX-атрибуты и дочерние элементы в один объект и передаёт их этому компоненту.  Этот объект называется «пропсы» (props) (то есть содержащий атрибуты и дочерние элементы)

>Базовый пример пропсов
1 Передаём React-элемент <Welcome name="Алиса" /> в ReactDOM.render().
2 React вызывает компонент Welcome с пропсами {name: 'Алиса'}.
3 Компонент Welcome возвращает элемент <h1>Привет, Алиса</h1> в качестве результата.
4 React DOM делает минимальные изменения в DOM, чтобы получилось <h1>Привет, Алиса</h1>.


```
function Welcome(props) {  return <h1>Привет, {props.name}</h1>;
}

const element = <Welcome name="Алиса" />;ReactDOM.render(
  element,
  document.getElementById('root')
);
```

Также PROPS это атрибуты, которые можно создавать в реакте.
Синтаксис атрибутов похож на синтаксис input,
<input id="root" placeholder="hello" ...>

Когда такой атрибут создается в "описании" карточки <Card /> то в параметрах функции Card(props) они переходят как объекты.
К примеру, <Card name ="my name"/>
будет при вызове Card (props) делаться объектом. 
Object (name: "my name")
name:"my name"

Это значит, что атрибут name доступен через props.name

Пример.
=1_Создается компонент

function Card (props){
  return( 
  <div>
  <h2>{props.img}</h2>
  <img src={props.img} alt="avatar_1" /> 
  alt={props.alt}
  <p>{props.phone}</p>
  </div>)
};

=2_Рендерится с атрибутами \ пропсами
ReactDOM.render(
  <div>
  <Card 
  name="my name" 
  img="3fsf" 
  email="esdf@skfdgjh.fg" 
  alt="alt" 
  phone="phone"/>
  </div>,
  document.getElementById("root")
);

===


#### Композиция элементов
Компоненты могут ссылаться на другие компоненты в возвращённом ими дереве. Это позволяет  использовать одну и ту же абстракцию — компоненты — на любом уровне приложения. Неважно, пишем ли мы кнопку, форму или целый экран: все они, как правило, представляют собой компоненты в React-приложениях.
> Например, компонент App может отрендерить компонент Welcome несколько раз:

```
function Welcome(props) { 
  return <h1>Привет, {props.name}</h1>;
} -\\код компонента-функции. То есть сам компонент.

function App() {
  return (
    <div>
      <Welcome \\ объявление компонент-функция
      name="Алиса" /> \\ пропс
      <Welcome \\ объявление компонент-функция
      name="Базилио" />  \\ пропс
      <Welcome \\ объявление компонент-функция
      name="Буратино" /> \\ пропс
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```
#### Извлечение компонентов 
Компоненты можно разделять на части

#### Импорт
Компоненты принято импортировать.
>Для этого:
- создается новый файл с названием компонента (в папке src):
Heading.jsx
-там помещается компонент
- помещается код импорта реакта в начало компонента
import React from "react"; 
-в конце кода в файле компонента помещается код экспорта
export default Heading;
- в файле index.js помещается код импорта
import Heading from "./Heading.jsx" (часто можно не указывать расширение)

Пример.
```
Файл index

import React from "react";
import ReactDOM from "react-dom";
import Heading from "./Heading.jsx" 
import List from "./List.jsx" 

ReactDOM.render(
  <div>
   <Heading />
   <List /> 
  </div>,
  document.getElementById("root")
);
```
=== Файл компонента <Heading />
```
import React from "react";

function Heading()
{
  return <h1>My Favourite Foods</h1>;
}

export default Heading;
```
=== Файл компонента <List /> 
```
import React from "react";

function List()
{
return <ul><li>Bacon</li><li>Jamon</li><li>Noodles</li></ul>;
}

export default List;
```
=== ИЛИ
```
import React from "react";

function List(){
return (
  <ul>
  <li>Bacon</li>
  <li>Jamon</li>
  <li>Noodles</li>
  </ul>
  );
}

export default List;
```
9---- Имопрт ES6

Файл (1) - куда импортируют
```
import React from "react";
import ReactDOM from "react-dom";
import pi, { doublePi, triplePi } from "./math.js";

ReactDOM.render(
  <ul>
    <li>{pi}</li>
    <li>{doublePi()}</li>
    <li>{triplePi()}</li>
  </ul>,
  document.getElementById("root")
);
```
Файл (2) - откуда импортируют
```
const pi = 3.1415962;

function doublePi() {
  return pi * 2;
}

function triplePi() {
  return pi * 3;
}

export default pi;
export { doublePi, triplePi };
```
======= 2-й пример импорта \ экспорта 
(1) файл - куда импортируется
```
import React from "react";
import ReactDOM from "react-dom";
import { add, multiply, subtract, divide} from "./calculator.js"

//Import the add, multiply, subtract and divide functions
//from the calculator.js file.
//If successful, your website should look the same as the Final.png

ReactDOM.render(
  <ul>
    <li>{add(1, 2)}</li>
    <li>{multiply(2, 3)}</li>
    <li>{subtract(7, 2)}</li>
    <li>{divide(5, 2)}</li>
  </ul>,
  document.getElementById("root")
);
```
(2) файл - откуда экспортируется
```
function add(n1, n2) {
  return n1 + n2;
}

function multiply(n1, n2) {
  return n1 * n2;
}

function subtract(n1, n2) {
  return n1 - n2;
}

function divide(n1, n2) {
  return n1 / n2;
}

export { add, multiply, subtract, divide};
```
======= Приложение keeper
```
= Файл App.jsx

import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";

function App() {
  return (
    <div>
      <Header />
      <Note />
      <Footer />
    </div>
  );
}

export default App;
```
= Файл Footer.jsx
```
import React from "react";

function Footer() {
  const currentYear = new Date().getFullYear();
  return (
    <footer>
      <p>Copyright ? {currentYear}</p>
    </footer>
  );
}

export default Footer;
```

= Файл Header.jsx
```
import React from "react";

function Header() {
  return (
    <header>
      <h1>Keeper</h1>
    </header>
  );
}

export default Header;
```
= Файл Note.jsx
```
import React from "react";

function Note() {
  return (
    <div className="note">
      <h1>This is the note title</h1>
      <p>This is the note content</p>
    </div>
  );
}

export default Note;
```


> чтобы экспортировать из файла в виде массива с внутренними объектами

```
const contacts = [
  {
    name: "Beyonce",
    imgURL:
      "https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg",
    phone: "+123 456 789",
    email: "b@beyonce.com"
  },
  {
    name: "Jack Bauer",
    imgURL:
      "https://pbs.twimg.com/profile_images/625247595825246208/X3XLea04_400x400.jpg",
    phone: "+987 654 321",
    email: "jack@nowhere.com"
  },
  {
    name: "Chuck Norris",
    imgURL:
      "https://i.pinimg.com/originals/e3/94/47/e39447de921955826b1e498ccf9a39af.png",
    phone: "+918 372 574",
    email: "gmail@chucknorris.com"
  }
];
export default contacts;
```

нужно использовать следующий код
```
import React from "react";
import Card from "./Card.jsx";
import contacts from "../contacts.js"

console.log(contacts);

function App() {
  return( 
    <div>
    <h1 className="heading">My contacts</h1>
    <Card
    name={contacts[0].name} 
    src={contacts[0].imgURL}
    phone={contacts[0].phone}
    email={contacts[0].email} />
    </div>);
}

export default App;
```

#### Метод map

Вместо 
```
<Card
        name={contacts[0].name}
        img={contacts[0].imgURL}
        tel={contacts[0].phone}
        email={contacts[0].email}
      />
      <Card
        name={contacts[1].name}
        img={contacts[1].imgURL}
        tel={contacts[1].phone}
        email={contacts[1].email}
      />
      <Card
        name={contacts[2].name}
        img={contacts[2].imgURL}
        tel={contacts[2].phone}
        email={contacts[2].email}
      />
```
= Можно использовать функцию map (contacts это переменная в виде массива с объектами-элементами)
```
  const contacts = [
  {
    id: 1,
    name: "Beyonce",
    imgURL:
      "https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg",
    phone: "+123 456 789",
    email: "b@beyonce.com"
  },
  {
    id: 2,
    name: "Jack Bauer",
    imgURL:
      "https://pbs.twimg.com/profile_images/625247595825246208/X3XLea04_400x400.jpg",
    phone: "+987 654 321",
    email: "jack@nowhere.com"
  },
  {
    id: 3,
    name: "Chuck Norris",
    imgURL:
      "https://i.pinimg.com/originals/e3/94/47/e39447de921955826b1e498ccf9a39af.png",
    phone: "+918 372 574",
    email: "gmail@chucknorris.com"
  }
];
```
  \\создается функция для создания карточки в App.jsx
  
```
  function createCard()
  {
  return <Card 
  name={contact.name};
  />
  }
```
  \\ Создается map-функция
```
 function createCard(contact){
  return <Card
  key={contact.id}
  name={contact.name} 
  img={contact.imgURL} 
  tel={contact.phone}
  email={contact.email}
  />
}
```

############# Mapping Components Practice
```
Import React from "react";

function App() {
  return (
    <div>
      <h1>
        <span>emojipedia</span>
      </h1>

      <dl className="dictionary">
        <div className="term">
          <dt>
            <span className="emoji" role="img" aria-label="Tense Biceps">
              ??
            </span>
            <span>Tense Biceps</span>
          </dt>
          <dd>
            “You can do that!” or “I feel strong!” Arm with tense biceps. Also
            used in connection with doing sports, e.g. at the gym.
          </dd>
        </div>
        <div className="term">
          <dt>
            <span className="emoji" role="img" aria-label="Tense Biceps">
              ??
            </span>
            <span>Person With Folded Hands</span>
          </dt>
          <dd>
            Two hands pressed together. Is currently very introverted, saying a
            prayer, or hoping for enlightenment. Is also used as a “high five”
            or to say thank you.
          </dd>
        </div>
        <div className="term">
          <dt>
            <span className="emoji" role="img" aria-label="Tense Biceps">
              ??
            </span>
            <span>Rolling On The Floor, Laughing</span>
          </dt>
          <dd>
            This is funny! A smiley face, rolling on the floor, laughing. The
            face is laughing boundlessly. The emoji version of “rofl“. Stands
            for „rolling on the floor, laughing“.
          </dd>
        </div>
      </dl>
    </div>
  );
}

export default App;

const emojipedia = [
  {
    id: 1,
    emoji: "??",
    name: "Tense Biceps",
    meaning:
    "“You can do that!” or “I feel strong!” Arm with tense biceps. Also used in connection with doing sports, e.g. at the gym."
  },
  {
    id: 2,
    emoji: "??",
    name: "Person With Folded Hands",
    meaning:
    "Two hands pressed together. Is currently very introverted, saying a prayer, or hoping for enlightenment. Is also used as a “high five” or to say thank you."
  },
  {
    id: 3,
    emoji: "??",
    name: "Rolling On The Floor, Laughing",
    meaning:
    "This is funny! A smiley face, rolling on the floor, laughing. The face is laughing boundlessly. The emoji version of “rofl“. Stands for „rolling on the floor, laughing“."
  }
];

import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));
```

===================================
#### Динамическое создание карточки
===================================

1) в app. js
```
import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import notes from "../notes";

function App() {
  return (
     <div>
     <Header />
     {notes.map((noteItem =>
<Note 
key={noteItem.key}
title={noteItem.title}
content={noteItem.content}
/>
))}
    <Footer />
    </div>
  );
}

export default App;
```
2) в Note.js
```
import React from "react";

function Note(props) {
  return (
    <div className="note">
      <h1>{props.title}</h1>
      <p>{props.content}</p>
    </div>
  );
}

export default Note;
```
3) в notes.js
```
const notes = [
  {
    key: 1,
    title: "Delegation",
    content:
    "Q. How many programmers does it take to change a light bulb? A. None – It’s a hardware problem"
  },
  {
    key: 2,
    title: "Loops",
    content:
    "How to keep a programmer in the shower forever. Show him the shampoo bottle instructions: Lather. Rinse. Repeat."
  },
  {
    key: 3,
    title: "Arrays",
    content:
    "Q. Why did the programmer quit his job? A. Because he didn't get arrays."
  },
  {
    key: 4,
    title: "Hardware vs. Software",
    content:
    "What's the difference between hardware and software? You can hit your hardware with a hammer, but you can only curse at your software."
  }
];

export default notes;
```

#### Состояние (State) и жизненный цикл (lifecycle)

> «Состояние» очень похоже на пропсы, отличие в том, что состояние контролируется и доступно только конкретному компоненту.

Преобразование функционального компонента в классовый

Преобразование функционального компонента Clock в классовый компонент за 5 шагов:
```
unction Clock(props) {
  return (
    <div>
    <h1>Привет, мир!</h1>
    <h2>Сейчас {props.date.toLocaleTimeString()}.
    </h2> 
    </div>  );
}

function tick() {
  ReactDOM.render(
    <Clock date={new Date()} />,    document.getElementById('root')
  );
}

setInterval(tick, 1000);
```


1 Создаём ES6-класс с таким же именем, указываем React.Component в качестве родительского класса
2 Добавим в класс пустой метод render()
3 Перенесём тело функции в метод render()
4 Заменим props на this.props в теле render()
5 Удалим оставшееся пустое объявление функции
```
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Привет, мир!</h1>
        <h2>Сейчас {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```
Теперь Clock определён как класс, а не функция.
Метод render будет вызываться каждый раз, когда происходит обновление. Так как мы рендерим <Clock /> в один и тот же DOM-контейнер, мы используем единственный экземпляр класса Clock — поэтому мы можем задействовать внутреннее состояние и методы жизненного цикла.

Метод render будет вызываться каждый раз, когда происходит обновление. Так как мы рендерим <Clock /> в один и тот же DOM-контейнер, мы используем единственный экземпляр класса Clock — поэтому мы можем задействовать внутреннее состояние и методы жизненного цикла.

> В приложениях со множеством компонентов очень важно освобождать используемые системные ресурсы, когда компоненты удаляются.
Первоначальный рендеринг компонента в DOM называется «монтирование» (mounting). Нам нужно устанавливать таймер всякий раз, когда это происходит.
Каждый раз когда DOM-узел, созданный компонентом, удаляется, происходит «размонтирование» (unmounting). Чтобы избежать утечки ресурсов, мы будем сбрасывать таймер при каждом «размонтировании».
Объявим специальные методы, которые компонент будет вызывать при монтировании и размонтировании. Эти методы называются «методами жизненного цикла» (lifecycle methods).

```
componentDidMount() {  }
componentWillUnmount() {  }
```
> Правила использования State
1 Не изменяnm состояние напрямую 

Неправильно
`this.state.comment = 'Привет';`

Вместо этого используйте setState():

Правильно
`this.setState({comment: 'Привет'});`

> 2 Обновления состояния могут быть асинхронными
React может сгруппировать несколько вызовов setState() в одно обновление для улучшения производительности.
Поскольку this.props и this.state могут обновляться асинхронно,  можно не полагаться на их текущее значение для вычисления следующего состояния.
3  Обновления состояния объединяются. Когда мы вызываем setState(), React объединит аргумент (новое состояние) c текущим состоянием. Их можно обновлять по отдельности с помощью отдельных вызовов setState().
Например, состояние может состоять из нескольких независимых полей.


Чтобы проверить статус изменений  и рендерить разные блоки разметки в зависимости от этого есть 2 способа
```
1) простой функцией

import React from "react";
var isLoggedIn = false;

function conditionCheck (){
  if (isLoggedIn === true) {
  return (<h1>Hello</h1>)
  } else {
    return(
    <form className="form">
    <input type="text" placeholder="Username" />
    <input type="password" placeholder="Password" />
    <button type="submit">Login</button>
    </form>)
  }
}

function App() {
  return (
    <div className="container">
     {conditionCheck ()}     
    </div>
  );
}

export default App;
```
2) 
```
import React from "react";
import Login from "./Login";

var isLoggedIn = false;

const currentTime = new Date(2019, 11, 1, 9).getHours();
console.log(currentTime);

function App() {
  return (
    <div className="container">
      {/*Ternary Operator*/}
      {isLoggedIn ? <h1>Hello</h1> : <Login />}
      {/*AND Operator*/}
      {currentTime > 12 && <h1>Why are you still working?</h1>}
    </div>
  );
}

export default App;

import React from "react";

function Input(props) {
  return <input type={props.type} placeholder={props.placeholder} />;
}

export default Input;

import React from "react";
import Input from "./Input";

function Login() {
  return (
    <form className="form">
      <Input type="text" placeholder="Username" />
      <Input type="password" placeholder="Password" />
      <button type="submit">Login</button>
    </form>
  );
}

export default Login;
```

useState
```
===Импорт - вариант 1

import React, { useState } from "react";

function App() {

  const state = useState(); 

}
```
===Импорт - вариант 2
```
import React from "react";

function App() {
  const state = React.useState(); 
}
```

#### Однонаправленный поток данных 
В иерархии компонентов ни родительский, ни дочерние компоненты не знают, задано ли состояние другого компонента. Также не важно, как был создан определённый компонент — с помощью функции или с помощью класса.
Состояние часто называют «локальным», «внутренним» или инкапсулированным. Оно доступно только для самого компонента и скрыто от других.
Компонент может передать своё состояние вниз по дереву в виде пропсов дочерних компонентов:

`<FormattedDate date={this.state.date} />`
Состояние всегда принадлежит определённому компоненту, а любые производные этого состояния могут влиять только на компоненты, находящиеся «ниже» в дереве компонентов.

#### Обработка событий

Обработка событий в React-элементах очень похожа на обработку событий в DOM-элементах. Но есть несколько синтаксических отличий:

- События в React именуются в стиле camelCase вместо нижнего регистра.
- С JSX вы передаёте функцию как обработчик события вместо строки.
- Ещё одно отличие — в React нельзя предотвратить обработчик события по умолчанию, вернув false. Нужно явно вызвать preventDefault
- При использовании React обычно не нужно вызывать addEventListener, чтобы добавить обработчики в DOM-элемент после его создания. Вместо этого добавьте обработчик сразу после того, как элемент отрендерился.

Например, в HTML:
```
<button onclick="activateLasers()">
  Активировать лазеры
</button>
```
В React немного иначе:
```
<button onClick={activateLasers}>  Активировать лазеры
</button>
```

При обращении к this в JSX-колбэках необходимо учитывать, что методы класса в JavaScript по умолчанию не привязаны к контексту. 
Обычно, если ссылаться на метод без () после него, например, onClick={this.handleClick}, этот метод нужно привязать.

Если не использовать bind, существует два других способа. 1) экспериментальный синтаксис общедоступных полей классов, 2) стрелочные функции в колбэке. (см. примеры в документации)

#### Передача аргументов в обработчики событий

Внутри цикла часто нужно передать дополнительный аргумент в обработчик события. Например, если id — это идентификатор строки, можно использовать следующие варианты:
```
<button onClick={(e) => this.deleteRow(id, e)}>Удалить строку</button>
<button onClick={this.deleteRow.bind(this, id)}>Удалить строку</button>
```
Две строки выше — эквивалентны, и используют стрелочные функции и Function.prototype.bind соответственно.

В обоих случаях аргумент e, представляющий событие React, будет передан как второй аргумент после идентификатора. Используя стрелочную функцию, необходимо передавать аргумент явно, но с bind любые последующие аргументы передаются автоматически.

#### Условный рендеринг

React позволяет разделить логику на независимые компоненты. Эти компоненты можно показывать или прятать в зависимости от текущего состояния.

Условный рендеринг в React работает так же, как условные выражения работают в JavaScript. 
В таких ситуациях используется условный оператор JavaScript или выражения подобные if.

Пример:
```
function UserGreeting(props) {
  return <h1>С возвращением!</h1>;
}

function GuestGreeting(props) {
  return <h1>Войдите, пожалуйста.</h1>;
}
```

Можно создать компонент Greeting, который отражает один из этих компонентов в зависимости от того, выполнен ли вход на сайт:
````
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {    return <UserGreeting />;  }  return <GuestGreeting />;}
ReactDOM.render(
  // Попробуйте заменить на isLoggedIn={true} и посмотрите на эффект.
  <Greeting isLoggedIn={false} />,  document.getElementById('root'));
```

В этом примере рендерится различное приветствие в зависимости от значения пропа isLoggedIn

===================================
Хуки
===================================

В коде ниже
- загружается useState, с изначально введенными данными 123.
- эти 123 размещены в переменной count, которая идет передается по названию в h1.
- во время события onClick на кнопке вызывается функция increase, которая вызывает функцию setCount c заданными числами,
- при этом функция setCount это название функции в const, а сама функция зашита как вторая в useState, с неопределенным по умолчанию название. Она и изменяет первое значение 123 на 456.

"в функциональных компонентах в React хук useState возвращает [твоё значение, и функцию для его изменения] и менять нужно всегда через функцию в твоём примере (setCount)"

import React from "react";

function App() {

const [count, setCount] = React.useState(123);

function increase (){
setCount(456)
}

return(
  <div className="container">
    <h1>{count}</h1>
    <button onClick={increase}>+</button>
  </div>,
  document.getElementById("root")
);
}

export default App;

=======Код полный с урока=======

import React, { useState } from "react";

function App() {
  const [count, setCount] = useState(0);

  function increase() {
    setCount(count + 1);
  }

  function decrease() {
    setCount(count - 1);
  }

  return (
    <div className="container">
      <h1>{count}</h1>
      <button onClick={decrease}>-</button>
      <button onClick={increase}>+</button>
    </div>
  );
}

export default App;

======= Практика useState ========
Код обновляет время каждую секунду
================================

import React, { useState } from "react";

function App() {
  setInterval(updateTime, 1000);

  const now = new Date().toLocaleTimeString();

  const [time, setTime] = useState(now);

  function updateTime() {
    const newTime = new Date().toLocaleTimeString();
    setTime(newTime);
  }

  return (
    <div className="container">
      <h1>{time}</h1>
      <button onClick={updateTime}>Get Time</button>
    </div>
  );
}

export default App;

======= Пример кода с useState =======
\\ меняет текст в h1

import React, { useState } from "react";

function App() {

const [headingText, setHeadingText] = useState("Hello");

  function clickFunc(){
    setHeadingText("Its a Good day for pray");
  };

  return (
    <div className="container">
      <h1>{headingText}</h1>
      <input type="text" placeholder="What's your name?" />
      <button onClick={clickFunc}>Submit</button>
    </div>
  );
}

export default App;

=======  Смена цвета кнопки в зависимости от события =======

import React, { useState } from "react";

function App() {

const [isMouseOver, setMouseOver] = useState(false);

function changeColorEvent(){
  setMouseOver(true);
};

function returnColorEvent(){
  setMouseOver(false);
}

  return (
    <div className="container">
      <h1>Hello</h1>
      <input type="text" placeholder="What's your name?" />
      <button id="button1" 
      style = {{backgroundColor: isMouseOver ? "black" : "white"}}
      onMouseOver={changeColorEvent}
      onMouseOut={returnColorEvent}
      >Submit</button>
      
    </div>
  );
}

export default App;

=======
Формы
=======

При добавлении события onChange к форме или других действий в движке при работе с формой создается объект.

Значит, можно использовать методы к объектам.
К примеру, 

<input onChange={Change_funct} type="text" place

 function Change_funct(event){
  console.log(event.target.value);
  console.log(event.target.placeholder);
  console.log(event.target.type);
}

Логирует введенные данные пользователем, плейсхолдер и тип данных

= Чтобы вывести введенные пользователем данные на сайт, нужно
1) сделать useState

const [name, setName] = useState (" ");

2) в разметку в нужном месте добавляем переменную {name}

3) в функцию, выполняемую в связи с событием инпута добавляем функцию из useState c event.target.value.

import React, {useState} from "react";

function App() {

  const [name, setName] = useState (" ");

 function Change_funct(event)
 {
  setName(event.target.value);
 }

  return (
    <div className="container">
      <h1>Hello {name}</h1>
      <input 
      onChange={Change_funct}
      type="text" placeholder="What's your name?" 
      value={name}/>
      <button>Submit</button>
    </div>
  );
}

export default App;

При этом в реакте необходимо использовать единое место для хранения значения инпута, в виде переменной из useState (концепция controlled component).

======= Для того, чтобы введенное в инпут имя вводилось только после нажатия кнопки необходим следующий код с 2мя useState.

Важно сохранять слушатель onChange, так как ввод идет через него.

=======
import React, {useState} from "react";

function App() {

const [V_name, F_setName] = useState (" ");
const [V_headText, F_updateHeadText] = useState (" ");

function F_changeName(event)
{
 F_setName(event.target.value);
}

function F_click()
{
 F_updateHeadText(V_name)
}

  return (
    <div className="container">
      <h1>Hello {V_headText}</h1>
      <input
      onChange={F_changeName}
      type="text" placeholder="What's your name?" 
      value={V_name}
      />
      <button onClick={F_click}>Submit</button>
    </div>
  );
}

export default App;
=======

Если инпут будет обернут в тэг <form/>, на которую создан слушатель F_click (а не на инпут), то следует использовать следующий метод. 
Это необходимо так как стандартное поведение формы это перезагрузка формы после введения в нее данных.

function F_click(event) 
{
    F_updateHeadText(V_name);
    event.preventDefault();
}

======= Задание по обновлению первого и второго имени по событию onSubmit =======

\\ Подробный вариант

import React, { useState } from "react";

function App() {
  const [V_name, F_setInputName] = useState(" ");
  const [V_updateName, F_updateName] = useState(" ");

  const [V_surname, F_setInputSurname] = useState(" ");
  const [V_updateSurname, F_updateSurname] = useState(" ");

  function F_changeName(event) {
    F_setInputName(event.target.value);
  }

  function F_changeSurname(event) {
    F_setInputSurname(event.target.value);
  }

  function F_click(event) {
    F_updateName(V_name);
    F_updateSurname(V_surname);
    event.preventDefault();
  }

  return (
    <div className="container">
    <h1>Hello {V_updateName} {V_updateSurname}</h1>
    <form onSubmit={F_click}>
    <input
       onChange={F_changeName}
       name="fName"
       placeholder="First Name"
       value={V_name}
     />
     <input
       onChange={F_changeSurname}
       name="lName"
       placeholder="Last Name"
       value={V_surname}
     />
       <button>Submit</button>
    </form>
    </div>
  );
}

export default App;

\\ Короткий вариант (использование объектов в качестве параметра useState и единой функции для обновления их значений). JS распознает какой именно инпут был изменен через event.target.name (const inputName = event.target.name). Однако, реакт рендерит заново все инпуты, заменяя первый вторым и наоборот и через простую функцию if else решить проблему не получится. Следует запоминать "старое название" не измененного инпута, и устаналивать новое для нужного. Конструкция выглядит следующим образом (с деструктуризацией переменной в виде объекта)

import React, { useState } from "react";

function App() {
  const [fullName, setFullName] = useState({
    fName: "",
    lName: ""
  });

  function handleChange(event) {
    const { value, name } = event.target;

    setFullName(prevValue => {
      if (name === "fName") {
        return {
          fName: value,
          lName: prevValue.lName
        };
      } else if (name === "lName") {
        return {
          fName: prevValue.fName,
          lname: value
        };
      }
    });
  }

  return (
    <div className="container">
      <h1>
        Hello {fullName.fName} {fullName.lName}
      </h1>
      <form>
        <input
          name="fName"
          onChange={handleChange}
          placeholder="First Name"
          value={fullName.fName}
        />
        <input
          name="lName"
          onChange={handleChange}
          placeholder="Last Name"
          value={fullName.lName}
        />
        <button>Submit</button>
      </form>
    </div>
  );
}

export default App;

======= Обновление 3х инпутов

import React, { useState } from "react";

function App() {
  const [contact, setContact] = useState({
    fName: "",
    lName: "",
    email: ""
  });

  function F_changeContact(event) {
    const { value, name } = event.target;
    
    setContact((prevValue) => {
      if (name === "fName") {
        return {
          fName: value,
          lName: prevValue.lName,
          email: prevValue.email
        };
      } else if (name === "lName") {
        return {
          fName: prevValue.fName,
          lname: value,
          email: prevValue.email
        };
      } else if (name === "email") {
        return {
          fName: prevValue.email,
          lname: prevValue.lName,
          email: value
        };
      }
    });
  }

  return (
    <div className="container">
      <h1>
        Hello {contact.fName} {contact.lName}
      </h1>
      <p>{contact.email}</p>
      <form>
        <input
          onChange={F_changeContact}
          name="fName"
          placeholder="First Name"
          value={contact.fName}
        />
        <input
          onChange={F_changeContact}
          name="lName"
          placeholder="Last Name"
          value={contact.lName}
        />
        <input
          onChange={F_changeContact}
          name="email"
          placeholder="Email"
          value={contact.email}
        />
        <button>Submit</button>
      </form>
    </div>
  );
}

export default App;

========
spreadOperator
========
сокращенный код с использованием оператора выглядит так:
prevValue - это объект, поэтому он позволяет дополнить его через оператор прошлый значением, добавив
новое название там где оно необходимо.

import React, { useState } from "react";

function App() {
  const [contact, setContact] = useState({
    fName: "",
    lName: "",
    email: ""
  });

function handleChange(event) {
const { name, value } = event.target;

setContact(prevValue => {
        return {
        ...prevValue,
        [name]: value
        };
    });
}

return (
    <div className="container">
      <h1>
        Hello {contact.fName} {contact.lName}
      </h1>
      <p>{contact.email}</p>
      <form>
        <input
          onChange={handleChange}
          name="fName"
          value={contact.fName}
          placeholder="First Name"
        />
        <input
          onChange={handleChange}
          name="lName"
          value={contact.lName}
          placeholder="Last Name"
        />
        <input
          onChange={handleChange}
          name="email"
          value={contact.email}
          placeholder="Email"
        />
        <button>Submit</button>
      </form>
    </div>
  );
}

export default App;

=============
Создание  toDoList с добавление новых элементов при нажатии на кнопку
=============

import React, {useState} from "react";

function App() {

const [V_inputText, F_setValue] = useState("");
const [V_valueOnClick, F_setNewToDo] = useState([]);

function F_setOnChange (event) {
  F_setValue(event.target.value);
} 

\\ ниже spread функция, сохраняет  в массиве старое значение prevItems, которое находится в функции 
\\ F_setNewToDo исходная переменная которого  - в V_valueOnClick, и добавляет новое значение из переменной 
\\ V_inputText
\\ F_setValue(""); в конце функции очищает инпут от введенных значений.

function F_addItemOnClick (event){
  F_setNewToDo( (prevItems) => {
    return [...prevItems, V_inputText]
  });
  F_setValue("");
}

  return (
    <div className="container">
      <div className="heading">
        <h1>To-Do List</h1>
      </div>
      <div className="form">
        <input 
        type="text"
        onChange={F_setOnChange}
        value={V_inputText}/>
        <button onClick={F_addItemOnClick}>
          <span>Add</span>
        </button>
      </div>
      <div>
        <ul>
        \\ стрелочная функция map
         {V_valueOnClick.map(V_valueOnClickItem => <li>{V_valueOnClickItem}</li>)}
        </ul>
      </div>
    </div>
  );
}

export default App;

=======
Создание комплекса компонентов
=======

Функционал зачеркивания слова при клике на него
import React, {useState} from "react";

======= APP.jsx =======

import React, { useState } from "react";
import TodoItem from "./TodoItem"

function App() {
  const [inputText, setInputText] = useState("");
  const [items, setItems] = useState([]);

  function handleChange(event) {
    const newValue = event.target.value;
    setInputText(newValue);
  }

  function addItem() {
    setItems(prevItems => {
      return [...prevItems, inputText];
    });
    setInputText("");
  }

  return (
    <div className="container">
      <div className="heading">
        <h1>To-Do List</h1>
      </div>
      <div className="form">
        <input onChange={handleChange} type="text" value={inputText} />
        <button onClick={addItem}>
          <span>Add</span>
        </button>
      </div>
      <div>
        <ul>
          {items.map(todoItem => (
            <TodoItem
            text = {todoItem}
            />
          ))}
        </ul>
      </div>
    </div>
  );
}

export default App;

======= ToDoItem.jsx =======

function TodoItem(props)
{
  const [isOnClick, setIsOnClick] = useState(false);

  function textDecorationEvent(){
  setIsOnClick(prevValue => {
  return (!prevValue)
  });
}  
  
  return(<li 
  style = {{textDecoration: isOnClick ? "line-through" : "none"}}
  onClick = {textDecorationEvent}
  > {props.text} </li>)
}
export default TodoItem;

======= Для удаления компонента из массива

======= APP.jsx =======

import React, { useState } from "react";
import TodoItem from "./TodoItem";

function App() {
  const [inputText, setInputText] = useState("");
  const [items, setItems] = useState([]);

  function handleChange(event) {
    const newValue = event.target.value;
    setInputText(newValue);
  }

  function addItem() {
    setItems((prevItems) => {
      return [...prevItems, inputText];
    });
    setInputText("");
  }

  function deleteItem(id) {
    setItems(prevItems => {
      return prevItems.filter(
      (item, index) =>{
        return index !== id
      }
      )
    });
  }

  return (
    <div className="container">
      <div className="heading">
        <h1>To-Do List</h1>
      </div>
      <div className="form">
        <input onChange={handleChange} type="text" value={inputText} />
        <button onClick={addItem}>
          <span>Add</span>
        </button>
      </div>
      <div>
        <ul>
          {items.map((todoItem, index) => (
            <TodoItem
            key = {index}
            id = {index} 
            text = {todoItem} 
            onChecked = {deleteItem} />
          ))}
        </ul>
      </div>
    </div>
  );
}

export default App;

======= TodoItem.jsx =======

import React from "react";

function TodoItem(props){
 
  return(<li 
  onClick = {() => {
    props.onChecked(props.id)}}
  > {props.text} </li>)
}

export default TodoItem;


============
Практика использования дерева компонентов
============

======= App.jsx =======

import React, { useState } from "react";
import ToDoItem from "./ToDoItem";
import InputArea from "./InputArea";

function App() {
  const [items, setItems] = useState([]);

  function F_addItem(inputText) {
    setItems((prevItems) => {
      return [...prevItems, inputText];
    });
  }

  function F_deleteItem(id) {
    setItems((prevItems) => {
      return prevItems.filter((item, index) => {
        return index !== id;
      });
    });
  }

  return (
    <div className="container">
      <div className="heading">
        <h1>To-Do List</h1>
      </div>
      <InputArea prop_item={items} prop_addItem={F_addItem} />
      <div>
        <ul>
          {items.map((todoItem, index) => (
            <ToDoItem
              key={index}
              id={index}
              text={todoItem}
              onChecked={F_deleteItem}
            />
          ))}
        </ul>
      </div>
    </div>
  );
}

export default App;

======= InputArea.jsx =======

import React, { useState } from "react";

function InputArea(props) {
  const [inputText, setInputText] = useState("");

  function F_handleChange(event) {
    const newValue = event.target.value;
    setInputText(newValue);
  }

  return (
    <div className="form">
      <input onChange={F_handleChange} type="text" value={inputText} />
      <button
        onClick={() => {
          props.prop_addItem(inputText);
          setInputText("");
        }}
      >
        <span>Add</span>
      </button>
    </div>
  );
}

export default InputArea;

======= ToDoItem =======
\\ использование функции в диве позволяет не вызывать функцию сразу как только див будет прочитан, а
только с момента его задействования в результате события

import React from "react";

function ToDoItem(props) {
  return (
    <div
      onClick={() => {
        props.onChecked(props.id);
      }}
    >
      <li>{props.text}</li>
    </div>
  );
}

export default ToDoItem;

==================================
keepeApp 3 - стадия разработки
==================================
Задача

//CHALLENGE:
//1. Implement the add note functionality.
//- Create a constant that keeps track of the title and content.
//- Pass the new note back to the App.
//- Add new note to an array.
//- Take array and render seperate Note components for each item.

//2. Implement the delete note functionality.
//- Callback from the Note component to trigger a delete function.
//- Use the filter function to filter out the item that needs deletion.
//- Pass a id over to the Note component, pass it back to the App when deleting.

//This is the end result you're aiming for:
//https://pogqj.csb.app/

Исходный код

[1] app.jsx

import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {
  return (
    <div>
      <Header />
      <CreateArea />
      <Note key={1} title="Note title" content="Note content" />
      <Footer />
    </div>
  );
}

export default App;

[2] CreateArea.jsx

import React from "react";

function CreateArea() {
  return (
    <div>
      <form>
        <input name="title" placeholder="Title" />
        <textarea name="content" placeholder="Take a note..." rows="3" />
        <button>Add</button>
      </form>
    </div>
  );
}

export default CreateArea;

[3] Footer.jsx

import React from "react";

function Footer() {
  const year = new Date().getFullYear();
  return (
    <footer>
      <p>Copyright ? {year}</p>
    </footer>
  );
}

export default Footer;

[4] Header.jsx

import React from "react";

function Header() {
  return (
    <header>
      <h1>Keeper</h1>
    </header>
  );
}

export default Header;

[5] Note.jsx

import React from "react";

function Note(props) {
  return (
    <div className="note">
      <h1>{props.title}</h1>
      <p>{props.content}</p>
      <button>DELETE</button>
    </div>
  );
}

export default Note;

1 //- Create a constant that keeps track of the title and content.
//Создать переменную, которвая отслеживает изменения. 
В компоненте (!)

- Создается в виде объекта, так как в этом объекте 2 значения - тайтл и контент.
В противном случае создавать придется 2 переменные. 

- передается в разметку в виде note.title и note.content  

- создается слушатель onChange и функция для изменения этих переменных, 
function F_change(event). Функция передается в onChange в разметке. В качестве параметра - event

- создается деструктуризированный объект 
const { name, value } = event.target;

- в функции F_change вызывается функция setNote (useState).
в ней указывается 

setNote(prevNote => 
{
    return 
    {
     ...prevNote,
    [name]: value
    };
}

в данном случае устанавливается предыдущий note (prevNote),
возвращается существующий компонент Note,
где через spread оператор возвращаются уже записанные компоненты Note (...prevNote,), 
затем новая запись переменной name (в квадратных скобках пишется в виду требований синтаксиса) и ей устанавливатеся значение value из event.target.

//CreateArea.jsx

import React from "react";

function CreateArea() {
  const [note, setNote] = React.useState({
    title: "",
    content: ""
  });

  function F_change(event) {
    const { name, value } = event.target;

    setNote(prevNote => {
      return {
        ...prevNote,
        [name]: value
      };
    });
  }

  return (
    <div>
      <form>
        <input
          name="title"
          onChange={F_change}
          value={note.title}
          placeholder="Title"
        />
        <textarea
          name="content"
          onChange={F_change}
          value={note.content}
          placeholder="Take a note..."
          rows="3"
        />
        <button>Add</button>
      </form>
    </div>
  );
}

export default CreateArea;

2\\ - Pass the new note back to the App.
Из компонента CreateArea вернуть  данные из созданных переменных в app.jsx.

- на button в CreateArea вешается событие onClick при срабатывании которого данные передаются в функцию,которая передает данные в app.jsx - F_submitNote

- ей передается параметр event, в первую очередь чтобы использовать прерывание дефолтного поведения формы, которая перезагружается при срабатывании события "event.preventDefault();" в теле функции.

- чтобы передать данные в app.jsx в нем в компоненте CreateArea создается props (onAdd) со значанием функции F_addNote. Сама функция пишется в app.jsx.

- компоненту CreateArea передается параметр (props)

- в app.jsx в функцию F_submitNote передается props.onAdd()

- в CreateArea.jsx в функции F_submitNote() добавляется props.onAdd(); что означает вызов пропса onAdd c функций внутри, которая в app.jsx выполняет необходимый код (функцию F_addNote).

- в props.onAdd() в качестве параметра передается текущее значение объекта note ()
props.onAdd(note); 
С этого момент при клике на кнопку объект note передается в app.jsx

//CreateArea.jsx

import React from "react";

function CreateArea(props) {
  const [note, setNote] = React.useState({
    title: "",
    content: ""
  });

  function F_change(event) {
    const { name, value } = event.target;

    setNote(prevNote => {
      return {
        ...prevNote,
        [name]: value
      };
    });
  }

  function F_submitNote(event)
  {
    props.onAdd(note);
    event.preventDefault;
  }
  
  return (
    <div>
      <form>
        <input
          name="title"
          onChange={F_change}
          value={note.title}
          placeholder="Title"
        />
        <textarea
          name="content"
          onChange={F_change}
          value={note.content}
          placeholder="Take a note..."
          rows="3"
        />
        <button onClick ={F_submitNote}>Add</button>
      </form>
    </div>
  );
  
// app.jsx

import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {
  
  function F_addNote()
  {
    
  }
  
  return (
    <div>
      <Header />
      <CreateArea
      onAdd = {F_addNote}
      />
      <Note key={1} title="Note title" content="Note content" />
      <Footer />
    </div>
  );
}

export default App;
}

3 // Add new note to an array.

Добавлять новосозданные note в массив

- в app.jsx создается константа с пустым массивом
const [notes, F_setNotes] = React.useState([]); 

-  в созданной ранее функции F_addNote помещается созданный ранее массив и добавляемые в него объекты кодом

function F_addNote(newNote)
{
    F_setNotes(prevNotes => 
    {
       return [...prevNotes, newNote];
    })
};

// app.jsx

import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {

const [notes, F_setNotes] = React.useState([]); 

  function F_addNote(newNote)
  {
    F_setNotes(prevNotes => 
    {
        [...prevNotes, newNote];
    })
  };
  
  return (
    <div>
      <Header />
      <CreateArea
      onAdd = {F_addNote}
      />
      <Note key={1} title="Note title" content="Note content" />
      <Footer />
    </div>
  );
}

export default App;
}

4 //- Take array and render seperate Note components for each item.
Созданный массив из app.jsx рендерить отдельно в каждом компоненте Note для каждой отдельной карточки.

- через метод map необходимо пройтись по массиву notes

- вместо отдельного статичного компоненте Note ( <Note key={1} title="Note title" content="Note content" />) помещается код 
{notes.map((noteItem) => 
{
    return <Note
    title={noteItem.title},
    content={noteItem.content}
    />
})}


// app.jsx

import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {

const [notes, F_setNotes] = React.useState([]); 

  function F_addNote(newNote)
  {
    F_setNotes(prevNotes => 
    {
        [...prevNotes, newNote];
    })
  };
  
  return (
    <div>
      <Header />
      <CreateArea
      onAdd = {F_addNote}
      />
      {notes.map((noteItem) => 
      {
            return <Note
            title={noteItem.title},
            content={noteItem.content}
            />
     })}
    <Footer />
    </div>
  );
}

export default App;

//2. Implement the delete note functionality.
1 //- Callback from the Note component to trigger a delete function.
Из компонента Note сделать вызов для фиксирования функции delete

- в компоненте Note на кнопку требуется поместить обработчик onClick и создать функцию-обработчик

- в app.jsx требуется создать функцию, которая будет удалять компонент исходя из его id (F_deleteNote)
F_deleteNote передается через пропс onDelete в коде, который использует метод map для прохода через массив notes 
      {notes.map((noteItem) => 
      {
            return <Note
            title={noteItem.title},
            content={noteItem.content}
            onDelete={F_deleteNote}
            />
     })}

- в Note jsx в функции F_handleClick добавляется вызов пропса props.onDelete(), которая выполняется в app.jsx
-  в app.jsx в функции F_deleteNote вызывается функция setNotes с предыдущими notes и функцией filter 
(принимает в себя 3 аргумента
let newArray = arr.filter(callback(element[, index, [array]])[, thisArg])
element
Текущий обрабатываемый элемент в массиве.
indexНеобязательный
Индекс текущего обрабатываемого элемента в массиве.
arrayНеобязательный
Массив, по которому осуществляется проход.)
В коде это:

function F_deleteNote(id)
{
        setNotes(prevNotes => {
        return prev.Notes.filter((noteItem, index) => {
        return index !== id;
        })
    })
}

- в создаваемый Note добавляется параметр key и id - для того, чтобы связать id элемента и ключ, по которому можно будет его идентифицировать. 

// app.jsx

import React from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {

const [notes, F_setNotes] = React.useState([]); 

  function F_addNote(newNote)
  {
    F_setNotes(prevNotes => 
    {
        [...prevNotes, newNote];
    })
  };

function F_deleteNote(id)
{
        setNotes(prevNotes => {
        return prev.Notes.filter((noteItem, index) => {
        return index !== id;
        })
    })
}
  
  return (
    <div>
      <Header />
      <CreateArea
      onAdd = {F_addNote}
      />
      {notes.map((noteItem) => 
      {
            return <Note
            key = 
            id = 
            title={noteItem.title},
            content={noteItem.content}
            />
     })}
    <Footer />
    </div>
  );
}

export default App;

\\Note.jsx

import React from "react";

function Note(props) {

function F_handleClick()
{
    props.onDelete(props.id);
}

  return (
    <div className="note">
      <h1>{props.title}</h1>
      <p>{props.content}</p>
      <button onClick={F_handleClick}>DELETE</button>
    </div>
  );
}

export default Note;

3 //- Pass a id over to the Note component, pass it back to the App when deleting.
- id создается внутри функции map, которая поддерживает возможность создания id при переборе.
- в app.jsx вводится переменная index. которая является id и ключом для компонента Note
{notes.map((noteItem, index) => 
      {
            return <Note
            key = {index}
            id = {index}
            title={noteItem.title},
            content={noteItem.content}
            />
     })}

- в Notes.jsx в функции F_handleClick() передается пропс с id    
function F_handleClick()
{
    props.onDelete(props.id);
}

- чтобы очистить поле ввода после нажатия кнопки в компонетне CreateArea в функции 
F_submitNote передается после нажатия пустой объект

  function F_submitNote(event)
  {
    props.onAdd(note);
    setNote
    ({
        title: "",
        content: ""
    });
    event.preventDefault;
  }
  
============
ПОЛНЫЙ КОД
============

// app.jsx

import React, { useState } from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {
  const [notes, setNotes] = useState([]);

  function addNote(newNote) {
    setNotes(prevNotes => {
      return [...prevNotes, newNote];
    });
  }

  function deleteNote(id) {
    setNotes(prevNotes => {
      return prevNotes.filter((noteItem, index) => {
        return index !== id;
      });
    });
  }

  return (
    <div>
      <Header />
      <CreateArea onAdd={addNote} />
      {notes.map((noteItem, index) => {
        return (
          <Note
            key={index}
            id={index}
            title={noteItem.title}
            content={noteItem.content}
            onDelete={deleteNote}
          />
        );
      })}
      <Footer />
    </div>
  );
}

export default App;

// CreateArea.jsx

import React, { useState } from "react";

function CreateArea(props) {
  const [note, setNote] = useState({
    title: "",
    content: ""
  });

  function handleChange(event) {
    const { name, value } = event.target;

    setNote(prevNote => {
      return {
        ...prevNote,
        [name]: value
      };
    });
  }

  function submitNote(event) {
    props.onAdd(note);
    setNote({
      title: "",
      content: ""
    });
    event.preventDefault();
  }

  return (
    <div>
      <form>
        <input
          name="title"
          onChange={handleChange}
          value={note.title}
          placeholder="Title"
        />
        <textarea
          name="content"
          onChange={handleChange}
          value={note.content}
          placeholder="Take a note..."
          rows="3"
        />
        <button onClick={submitNote}>Add</button>
      </form>
    </div>
  );
}

export default CreateArea;

// Note.jsx

import React from "react";

function Note(props) {
  function handleClick() {
    props.onDelete(props.id);
  }

  return (
    <div className="note">
      <h1>{props.title}</h1>
      <p>{props.content}</p>
      <button onClick={handleClick}>DELETE</button>
    </div>
  );
}

export default Note;

#### Browser Routing
Простое переключение между страницами (рендер страниц в зависимости от выбранной - пример кода из NFT магазина)

```
import { BrowserRouter, Link, Switch, Route } from "react-router-dom";
function Header() {
  return (
    <BrowserRouter forceRefresh={true}>
      <div className="app-root-1">
        <header className="Paper-root AppBar-root AppBar-positionStatic AppBar-colorPrimary Paper-elevation4">
          <div className="Toolbar-root Toolbar-regular header-appBar-13 Toolbar-gutters">
            <div className="header-left-4"></div>
            <img className="header-logo-11" src={logo} />
            <div className="header-vertical-9"></div>
            <Link to="/">
              <h5 className="Typography-root header-logo-text">OpenD</h5>
            </Link>
            <div className="header-empty-6"></div>
            <div className="header-space-8"></div>
            <button className="ButtonBase-root Button-root Button-text header-navButtons-3">
              <Link to="/discover">Discover</Link>
            </button>
            <button className="ButtonBase-root Button-root Button-text header-navButtons-3">
              <Link to="/minter">Minter</Link>
            </button>
            <button className="ButtonBase-root Button-root Button-text header-navButtons-3">
              <Link to="/collection">My NFTs</Link>
            </button>
          </div>
        </header>
      </div>
      
      <Switch> \\ код, который позволяет переключаться между элементами 
        <Route exact path="/">
          <img className="bottom-space" src={homeImage} />
        </Route>
        <Route path="/discover">{listingGallery}</Route>
        <Route path="/minter">
          <Minter />
        </Route>
        <Route path="/collection">{userOwnedGallery}</Route>
      </Switch>
    </BrowserRouter>
  );
}
export default Header;
```
