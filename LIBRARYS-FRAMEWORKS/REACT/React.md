https://github.com/leonidlebedev/javascript-airbnb/tree/master/react

1 ---
//var React = require('react');
//var ReactDOM = require('react-dom');
// ����������, ����� 
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Hello There</h1>, document.getElementById('root'));
// ��������� render 
// 1) ��� ����������, 
// 2) ��� ����������,
// 3) callback, �� ���� ����� ������� ����� ���������

//��� ���� ����� ���:
var h1 = document.createElement('h1');
h1.innerHTML = 'HelloWorld';
document.getElementById('root').appendChild(h1);

������� � �������������� JSX - ���������� JS ����� ���������� Babel.

2 ---
//��� ���������� ���������� ��������� - �������� � div 

ReactDOM.render(
<div>
<h1>Hello</h1>
<p>There</p>
</div>,
document.getElementById("root"));

3 ---
// ����� ������� � html, ������ JSX, ��� JS, ����� �������� ��� � {}
// ������
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

//��� ����� ��������� ��������

ReactDOM.render(
  <div>
    <h1>Hello {name}!</h1>
    <p>Your lucker number is {{`${luckNumber} ${smthElse}`}</p>
  </div>,
  document.getElementById("root")
);

//<p>Your lucker number is {{`${luckNumber} ${smthElse}`}</p>
// ���������
// <p>Your lucker number is {luckNumber + " " + smthElse}</p> 

4---

//Create a react app from scratch.
//It should display 2 paragraph HTML elements.
//The paragraphs should say:
//Created by YOURNAME.
//Copyright CURRENTYEAR.
//E.g.
//Created by Angela Yu.
//Copyright 2019.

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

5---
// ��� ����, ����� ���� ������ ��� ������ � ������� ����� 
<script src="../src/index.js" type="text/JSX"></script>

6---
// ���������� ������ 
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

//� � �ss � �� �� �����

.img 
{
  width: 100px;
  height: 100px;
}

7--- ���������� ������ ������
- � �������� ��������� �������� (!) ��� ��� �������� ������ ���� � ���� JS ������� + ���� �������� ������

import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(<h1 style={{color:"red"}}>Hello World!</h1>, document.getElementById("root"));

- ����� ����������. � ���� ������ ��� ��������� css ����������� � ������ JS � � JSX ������� ����������

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

��� ��������� ���������� ������� ����� �������� ���������� ��� � JS

customStyle.color = "blue";

=======

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
let minutes = Data.getMinutes();
let nowIs; 
let Time = nowIs + " ������� �����: " + hour + ":" + minutes;
const Style = 
{
  color: "red",
}

// Render 

ReactDOM.render(
  <h1 style={Style} class="heading">{Time}</h1>,
  document.getElementById("root")
);

 // ����������� ������� �����, ������� ����� �����, ���� � �������
function now()

==== ����� ������� ���

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
let minutes = Data.getMinutes();
let Time = timeFunction() + " ������� �����: " + hour + ":" + minutes;
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

 // ����������� ������� �����, ������� ����� �����, ���� � �������
 function timeFunction(nowIs) {
   if (hour >= 24 || hour <= 1) {
      nowIs = "������ ����!";
      Time = nowIs;
      return Time;
      ;
  } else {
      nowIs = "������ �����!";
      Time = nowIs;
      return Time;
      ;
  }
}

====== ����� ������� �������

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

// ======= ���� ������ �����������
let greeting; 

let customStyle = {
  color: ""
 };

if (hour < 12)
{
  greeting = "������ ����.";
  customStyle.color = "blue";
}
else if (hour < 18)
{
  greeting = "������ ����.";
  customStyle.color = "green";
}
else 
{
  greeting = "������ �����.";
  customStyle.color = "black";
}
// ======= ��������� ����� ������ �����������

// ======= Render 
ReactDOM.render(
  <h1 className = "heading" style={customStyle}>{greeting}</h1>,
  document.getElementById("root")
);


8 --- ����������

������� �������, �������� ������� �� ��������� � �������-�����
� ������ ��� ���������� ����� ����, ������� �������� �����������

� �������, 

function Heading()
{
  return <h1>My Favourite Foods</h1>;
}

��� ����, ����� ������������ ��������� ��� ����� � ���� ��� ���
<Heading></Heading>

�� �����

<Heading />

���������� ������� �������������.
��� �����:
- ��������� ����� ���� � ��������� ���������� (� ����� src):
Heading.jsx
-��� ���������� ���������
- ���������� ��� ������� ������ � ������ ����������
import React from "react"; 
-� ����� ���� � ����� ���������� ���������� ��� ��������
export default Heading;
- � ����� index.js ���������� ��� �������
import Heading from "./Heading.jsx" (����� ����� �� ��������� ����������)

������.
���� index

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

=== ���� ���������� <Heading />
import React from "react";

function Heading()
{
  return <h1>My Favourite Foods</h1>;
}

export default Heading;

=== ���� ���������� <List /> 

import React from "react";

function List()
{
return <ul><li>Bacon</li><li>Jamon</li><li>Noodles</li></ul>;
}

export default List;

=== ���
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

9---- ������ ES6

���� (1) - ���� �����������

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

���� (2) - ������ �����������
const pi = 3.1415962;

function doublePi() {
  return pi * 2;
}

function triplePi() {
  return pi * 3;
}

export default pi;
export { doublePi, triplePi };

======= 2-� ������ ������� \ �������� 
(1) ���� - ���� �������������

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

(2) ���� - ������ ��������������
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

======= ���������� keeper
= ���� App.jsx

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

= ���� Footer.jsx

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


= ���� Header.jsx

import React from "react";

function Header() {
  return (
    <header>
      <h1>Keeper</h1>
    </header>
  );
}

export default Header;

= ���� Note.jsx

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

======= PROPS
��� ��������, ������� ����� ��������� � ������.
��������� ��������� ����� �� ��������� input,
<input id="root" placeholder="hello" ...>

����� ����� ������� ��������� � "��������" �������� <Card /> �� � ���������� ������� Card(props) ��� ��������� ��� �������.
� �������, <Card name ="my name"/>
����� ��� ������ Card (props) �������� ��������. 
Object (name: "my name")
name:"my name"

��� ������, ��� ������� name �������� ����� props.name

������.
=1_��������� ���������

function Card (props){
  return( 
  <div>
  <h2>{props.img}</h2>
  <img src={props.img} alt="avatar_1" /> 
  alt={props.alt}
  <p>{props.phone}</p>
  </div>)
};

=2_���������� � ���������� \ ��������
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
����� �������������� �� ����� � ���� ������� � ����������� ���������

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

����� ������������ ��������� ���

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

======= ����� map

������ 

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
      
= ����� ������������ ������� map (contacts ��� ���������� � ���� ������� � ���������-����������)

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

  \\��������� ������� ��� �������� �������� � App.jsx
  
  function createCard()
  {
  return <Card 
  name={contact.name};
  />
  }
  
  \\ ��������� map-�������
 function createCard(contact){
  return <Card
  key={contact.id}
  name={contact.name} 
  img={contact.imgURL} 
  tel={contact.phone}
  email={contact.email}
  />
}


############# Mapping Components Practice

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
            �You can do that!� or �I feel strong!� Arm with tense biceps. Also
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
            prayer, or hoping for enlightenment. Is also used as a �high five�
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
            face is laughing boundlessly. The emoji version of �rofl�. Stands
            for �rolling on the floor, laughing�.
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
    "�You can do that!� or �I feel strong!� Arm with tense biceps. Also used in connection with doing sports, e.g. at the gym."
  },
  {
    id: 2,
    emoji: "??",
    name: "Person With Folded Hands",
    meaning:
    "Two hands pressed together. Is currently very introverted, saying a prayer, or hoping for enlightenment. Is also used as a �high five� or to say thank you."
  },
  {
    id: 3,
    emoji: "??",
    name: "Rolling On The Floor, Laughing",
    meaning:
    "This is funny! A smiley face, rolling on the floor, laughing. The face is laughing boundlessly. The emoji version of �rofl�. Stands for �rolling on the floor, laughing�."
  }
];

import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));

===================================
������������ �������� ��������
===================================

1) � app. js

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

2) � Note.js

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

3) � notes.js

const notes = [
  {
    key: 1,
    title: "Delegation",
    content:
    "Q. How many programmers does it take to change a light bulb? A. None � It�s a hardware problem"
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

======= State

����� ��������� ������ ��������� 
� ��������� ������ ����� �������� � ����������� �� ����� ���� 2 �������

1) ������� ��������

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

2) 

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

======= useState
===������ - ������� 1

import React, { useState } from "react";

function App() {

  const state = useState(); 

}

===������ - ������� 2

import React from "react";

function App() {
  const state = React.useState(); 
}

===================================
����
===================================

� ���� ����
- ����������� useState, � ���������� ���������� ������� 123.
- ��� 123 ��������� � ���������� count, ������� ���� ���������� �� �������� � h1.
- �� ����� ������� onClick �� ������ ���������� ������� increase, ������� �������� ������� setCount c ��������� �������,
- ��� ���� ������� setCount ��� �������� ������� � const, � ���� ������� ������ ��� ������ � useState, � �������������� �� ��������� ��������. ��� � �������� ������ �������� 123 �� 456.

"� �������������� ����������� � React ��� useState ���������� [��� ��������, � ������� ��� ��� ���������] � ������ ����� ������ ����� ������� � ���� ������� (setCount)"

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

=======��� ������ � �����=======

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

======= �������� useState ========
��� ��������� ����� ������ �������
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

======= ������ ���� � useState =======
\\ ������ ����� � h1

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

=======  ����� ����� ������ � ����������� �� ������� =======

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
�����
=======

��� ���������� ������� onChange � ����� ��� ������ �������� � ������ ��� ������ � ������ ��������� ������.

������, ����� ������������ ������ � ��������.
� �������, 

<input onChange={Change_funct} type="text" place

 function Change_funct(event){
  console.log(event.target.value);
  console.log(event.target.placeholder);
  console.log(event.target.type);
}

�������� ��������� ������ �������������, ����������� � ��� ������

= ����� ������� ��������� ������������� ������ �� ����, �����
1) ������� useState

const [name, setName] = useState (" ");

2) � �������� � ������ ����� ��������� ���������� {name}

3) � �������, ����������� � ����� � �������� ������ ��������� ������� �� useState c event.target.value.

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

��� ���� � ������ ���������� ������������ ������ ����� ��� �������� �������� ������, � ���� ���������� �� useState (��������� controlled component).

======= ��� ����, ����� ��������� � ����� ��� ��������� ������ ����� ������� ������ ��������� ��������� ��� � 2�� useState.

����� ��������� ��������� onChange, ��� ��� ���� ���� ����� ����.

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

���� ����� ����� ������� � ��� <form/>, �� ������� ������ ��������� F_click (� �� �� �����), �� ������� ������������ ��������� �����. 
��� ���������� ��� ��� ����������� ��������� ����� ��� ������������ ����� ����� �������� � ��� ������.

function F_click(event) 
{
    F_updateHeadText(V_name);
    event.preventDefault();
}

======= ������� �� ���������� ������� � ������� ����� �� ������� onSubmit =======

\\ ��������� �������

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

\\ �������� ������� (������������� �������� � �������� ��������� useState � ������ ������� ��� ���������� �� ��������). JS ���������� ����� ������ ����� ��� ������� ����� event.target.name (const inputName = event.target.name). ������, ����� �������� ������ ��� ������, ������� ������ ������ � �������� � ����� ������� ������� if else ������ �������� �� ���������. ������� ���������� "������ ��������" �� ����������� ������, � ������������ ����� ��� �������. ����������� �������� ��������� ������� (� ����������������� ���������� � ���� �������)

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

======= ���������� 3� �������

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
����������� ��� � �������������� ��������� �������� ���:
prevValue - ��� ������, ������� �� ��������� ��������� ��� ����� �������� ������� ���������, �������
����� �������� ��� ��� ��� ����������.

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
��������  toDoList � ���������� ����� ��������� ��� ������� �� ������
=============

import React, {useState} from "react";

function App() {

const [V_inputText, F_setValue] = useState("");
const [V_valueOnClick, F_setNewToDo] = useState([]);

function F_setOnChange (event) {
  F_setValue(event.target.value);
} 

\\ ���� spread �������, ���������  � ������� ������ �������� prevItems, ������� ��������� � ������� 
\\ F_setNewToDo �������� ���������� ��������  - � V_valueOnClick, � ��������� ����� �������� �� ���������� 
\\ V_inputText
\\ F_setValue(""); � ����� ������� ������� ����� �� ��������� ��������.

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
        \\ ���������� ������� map
         {V_valueOnClick.map(V_valueOnClickItem => <li>{V_valueOnClickItem}</li>)}
        </ul>
      </div>
    </div>
  );
}

export default App;

=======
�������� ��������� �����������
=======

���������� ������������ ����� ��� ����� �� ����
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

======= ��� �������� ���������� �� �������

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
�������� ������������� ������ �����������
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
\\ ������������� ������� � ���� ��������� �� �������� ������� ����� ��� ������ ��� ����� ��������, �
������ � ������� ��� �������������� � ���������� �������

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
keepeApp 3 - ������ ����������
==================================
������

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

�������� ���

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
//������� ����������, �������� ����������� ���������. 
� ���������� (!)

- ��������� � ���� �������, ��� ��� � ���� ������� 2 �������� - ����� � �������.
� ��������� ������ ��������� �������� 2 ����������. 

- ���������� � �������� � ���� note.title � note.content  

- ��������� ��������� onChange � ������� ��� ��������� ���� ����������, 
function F_change(event). ������� ���������� � onChange � ��������. � �������� ��������� - event

- ��������� ��������������������� ������ 
const { name, value } = event.target;

- � ������� F_change ���������� ������� setNote (useState).
� ��� ����������� 

setNote(prevNote => 
{
    return 
    {
     ...prevNote,
    [name]: value
    };
}

� ������ ������ ��������������� ���������� note (prevNote),
������������ ������������ ��������� Note,
��� ����� spread �������� ������������ ��� ���������� ���������� Note (...prevNote,), 
����� ����� ������ ���������� name (� ���������� ������� ������� � ���� ���������� ����������) � �� ��������������� �������� value �� event.target.

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
�� ���������� CreateArea �������  ������ �� ��������� ���������� � app.jsx.

- �� button � CreateArea �������� ������� onClick ��� ������������ �������� ������ ���������� � �������,������� �������� ������ � app.jsx - F_submitNote

- �� ���������� �������� event, � ������ ������� ����� ������������ ���������� ���������� ��������� �����, ������� ��������������� ��� ������������ ������� "event.preventDefault();" � ���� �������.

- ����� �������� ������ � app.jsx � ��� � ���������� CreateArea ��������� props (onAdd) �� ��������� ������� F_addNote. ���� ������� ������� � app.jsx.

- ���������� CreateArea ���������� �������� (props)

- � app.jsx � ������� F_submitNote ���������� props.onAdd()

- � CreateArea.jsx � ������� F_submitNote() ����������� props.onAdd(); ��� �������� ����� ������ onAdd c ������� ������, ������� � app.jsx ��������� ����������� ��� (������� F_addNote).

- � props.onAdd() � �������� ��������� ���������� ������� �������� ������� note ()
props.onAdd(note); 
� ����� ������ ��� ����� �� ������ ������ note ���������� � app.jsx

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

��������� ������������� note � ������

- � app.jsx ��������� ��������� � ������ ��������
const [notes, F_setNotes] = React.useState([]); 

-  � ��������� ����� ������� F_addNote ���������� ��������� ����� ������ � ����������� � ���� ������� �����

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
��������� ������ �� app.jsx ��������� �������� � ������ ���������� Note ��� ������ ��������� ��������.

- ����� ����� map ���������� �������� �� ������� notes

- ������ ���������� ���������� ���������� Note ( <Note key={1} title="Note title" content="Note content" />) ���������� ��� 
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
�� ���������� Note ������� ����� ��� ������������ ������� delete

- � ���������� Note �� ������ ��������� ��������� ���������� onClick � ������� �������-����������

- � app.jsx ��������� ������� �������, ������� ����� ������� ��������� ������ �� ��� id (F_deleteNote)
F_deleteNote ���������� ����� ����� onDelete � ����, ������� ���������� ����� map ��� ������� ����� ������ notes 
      {notes.map((noteItem) => 
      {
            return <Note
            title={noteItem.title},
            content={noteItem.content}
            onDelete={F_deleteNote}
            />
     })}

- � Note jsx � ������� F_handleClick ����������� ����� ������ props.onDelete(), ������� ����������� � app.jsx
-  � app.jsx � ������� F_deleteNote ���������� ������� setNotes � ����������� notes � �������� filter 
(��������� � ���� 3 ���������
let newArray = arr.filter(callback(element[, index, [array]])[, thisArg])
element
������� �������������� ������� � �������.
index��������������
������ �������� ��������������� �������� � �������.
array��������������
������, �� �������� �������������� ������.)
� ���� ���:

function F_deleteNote(id)
{
        setNotes(prevNotes => {
        return prev.Notes.filter((noteItem, index) => {
        return index !== id;
        })
    })
}

- � ����������� Note ����������� �������� key � id - ��� ����, ����� ������� id �������� � ����, �� �������� ����� ����� ��� ����������������. 

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
- id ��������� ������ ������� map, ������� ������������ ����������� �������� id ��� ��������.
- � app.jsx �������� ���������� index. ������� �������� id � ������ ��� ���������� Note
{notes.map((noteItem, index) => 
      {
            return <Note
            key = {index}
            id = {index}
            title={noteItem.title},
            content={noteItem.content}
            />
     })}

- � Notes.jsx � ������� F_handleClick() ���������� ����� � id    
function F_handleClick()
{
    props.onDelete(props.id);
}

- ����� �������� ���� ����� ����� ������� ������ � ���������� CreateArea � ������� 
F_submitNote ���������� ����� ������� ������ ������

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
������ ���
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


