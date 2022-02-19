// ******* ����������� ����������
const express = require("express");
const bodyParser = require("body-parser");
const ejs = require("ejs");
const mongoose = require("mongoose");

// ******* ����������� ��� �������
const app = express();
app.set('view engine', 'ejs');
app.use(bodyParser.urlencoded({extended: true}));
app.use(express.static("public"));

// ******* DB 
// ����������
mongoose.connect("mongodb://localhost:27017/wikiDB", { useNewUrlParser: true, useUnifiedTopology: true });
// DB �����
const postSchema = 
{
    title: String,
    content: String
};
// DB ������
const Post = mongoose.model("Post", postSchema);



// ******* �������� ������� �������
app.listen(3000, function() {
    console.log("Server started on port 3000");
});














* node
������ ����� ����� node
node index.js

***
REPL
***

����� ������ ���, �� ����� ������������ ��� � �������. 
����� � ���� ����� ������� node
�������� ������ >, ������, � ���.

> con

������ ��������� �� ������� ������ �������

> console.

��� ����������� ���� �������

> .exit
�����

��� 
***
ctrl + c
***

> clear 
�������� �������

* ��������� ������� � ��������� ������ �� ����������

const fs = require('fs');
��� fs ��� ���������, ����� - ���������� �� �� ����������� ������ � �������� ������ ������.

��� ���������� �������������� � ��������� ����� ���� ����� �������� �����������

//jshint esversion:6

*******
�������� ����������� ������� ��� NodeJS
*******

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

*******
NPM:
*******

�������� ������

* npm init
������ npm

����� ������� ����������� ��� ������, ������, ��������. Entry point - �������� �� �������� ���� JS, �������� �������, ����������� ���, � ��.

����� - �����������.

��������� ���� - package.json
(�������� ����� npm)

***
��������� �������
***

* ����� � ������ ���������� � npm init;
* npm install ��� ������ c ����� 
 (npm install superherous);
* � json ����� ��������� �����������;
* � index.js ����� ������� ���������� ��� node � ������������ ��� �� �������� �����������, 
������� ��������� �������� ������.
� �������, 
var superherous = require("superherous");

***
Node Express
***

���������
* ��������� ��������� ���� �������� 

$ mkdir myapp
$ cd myapp
$ npm init

* ��������� ��� ������������� npm entry point: (index.js) ��� ������ �������� ���� js � ���� ����������

* ����� $ npm install express

* � index.js ���� ����������:

const express = require("express");

* ������� ����������

const app = express();

* ������� ������� ��� ������

app.listen(3000);

��� ��� ����������� � �������

app.listen(3000, function() 
{
console.log('Server started on port 3000');
});

* ��������� � �������:

node index.js

* ��� ��������� ������� � ������ GET

���� ���� app.listen...

�������� ��� app.get("/", function (request, response) 
{

}
);

��� / ��� �������� ��������

������ (request, response) ����� ���� (req, res)

������

app.get("/", function(req, res) 
{
res.send('Hello World');
});

��� �������� �����, ������ ��� html ������� ������������ ����� 
sendFile

������:

app.get("/", function(req, res) 
{
res.sendFile(index.html);
});

��� �������� ����� � ����� ���� � ����� �� �����, ������� ������ � index.html ������� ������������ 
���������� __dirname

app.get("/", function(req, res) 
{
res.sendFile(__dirname + "index.html");
}); 

***
Nodemon
***

* ���������

$ npm install -g nodemon

* � ����������� ���������� ���������
$ nodemon index.js

***
�������� ������ �� �����
***

* ��� HTML ������ ���� ���������

(1)
<form action="index.html" method="post">
    <input type="text" name="num1" placeholder="First number">
    <input type="text" name="num2" placeholder="Second number">
    <button type="submit" name="submit">Calculate</button>
</form>

���

(2)
<form action="/" method="post">
    <input type="text" name="newItem">
    <button type="submit" name="submit">Add</button>
</form>

���

(3)
<form action="/" method="post">
    <input type="text" action="compose.ejs" name="postTitle">
    <button type="submit" name="submit"> Publish </button>
</form>

***
* � index.js ����������� ����� post

app.post("/", function(req, res)
{

}
);

* ��������������� node ������ bodyparser
$ npm install body-parser

* � index.js ������������� ���������� �� ����
const bodyParser = require("body-parser");

* ��������������� ���������� 
app.use(bodyParser.urlencoded({extended: true}));

����� ����� ����� �������� ������������ ����� req.body

��� ��������� ����� ������.

(1)
app.post("/", function(req, res)
{
var num1 = Number(req.body.num1);
var num2 = Number(req.body.num2);

var result = num1 + num2;

res.send(result);
});

���

(2)
app.post("/", function(req, res)
{
var item = req.body.newItem;
console.log(item)
});

���

(3)
app.post("/", function(req, res)
{
var composeInput = req.body.postTitle;
res.send(composeInput);
console.log(composeInput);
});

*******
������ ��� express � body-parser
*******

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

*******
������ ��� �������� html � ����������� �� ��� ������  
*******

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

*******
EJS
*******

$ npm i ejs

* �������� ��� app.use("view engine", "ejs");
����� �������� � ����� ��������� express

* ��������� ����� ���������� views � ����� �������

* � ��� ��������� ���� list.ejs ��� ������ ��������

* � ��� ���������� ���� html ���

* ��� html ���� ������������ ������ <%= %>

* ������ res.send ������������ ����� res.render

*** 
������
app.get("/", function(req, res)
{
var today = new Date();
var currentDay = today.getDay();
var day ="";

// ������� ��� ��������� ����
// ******************************************************************************
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

// ���� ������ if-else
// ******************************************************************************
// if (currentDay === 0)
// {
    //     day = "����.";
    // }
    // if else (currentDay === 1)
    // {
        //     day = "��.";
        // }
        // if else (currentDay === 2)
        // {
            //     day = "��.";
            // }
            // if else (currentDay === 3)
// {
//     day = "��.";
// }
// if else (currentDay === 4)
// {
//     day = "��.";
// }
// if else (currentDay === 5)
// {
//     day = "��.";
// }
// if else (currentDay === 6)
// {
//     day = "��.";
// }
// ******************************************************************************


switch (currentDay)
{
    case 0:
    day = "����.";
    break;
    
    case 1:
    day = "��.";
    break;

    case 2:
    day = "��.";
    break;

    case 3:
    day = "��.";
    break;

    case 4:
    day = "��.";
    break;

    case 5:
    day = "��.";
    break;

    case 6:
    day = "��.";
    break;

    console.log("Error: current day is equal to: " + currentDay);
}

res.render("list",{kindOfDay: day});

});

* ��� ��������� JS � HTML ������� ������������ <% %>

* ��� ��������� ������ ��������� ������ � express ������� ������� ����� public, ������� ����� ������������� express

* � app.js ������� �������� ��� ������������
app.use(express.static("public"));

***
������������� ������ �� ������ ������ ����� EJS (layout)
***

* ��������� ��������������� ���� 
footer.ejs ��� header.ejs

* � ��� ���������� ���, ������� ������������� body � ������ � ������������� body � ������.

* ��� ��������� ���� ����������� ��� � list.ejs 
<%- include("header") -%>  
<%- include("footer") -%> 

***
�������� �������
***

* ��������� ��������� ���� � ��������

* � app.js ��������� ����� ���������� � ��������� �����, � �������.

const date = require(__dirname + "date.js");    

* � ����� ����� ��������� ��� �������� �������. 

� �������

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

* ������ module.exports ����� ������������ exports. 

* ��� ������ ������� � ���������� �� ���� ������ �� ��������

� �������

let day = getDate();

* ��� ��������� �������������� �������, ����� �������� ���� ������� ��������� ������� ����� ������

module.exports.getDate = getDate;
� ������
module.exports.getDay = getDay;

� ��� �����.

* � app.js ����� ����� ����� �������� 

    let day = date.getDate();

    ���
    
    let day = date.getDay();
    
*******
����� ������������ ������   
*******

* util ��� ������ ���������� ������� � �������. � �������, ������� � ��������� obj

console.log(util.inspect(obj);

* console 

console.log - ����� �����

console.error - ����� ������

* EventEmmiter

var EventEmmiter = require("events").EventEmitter;
