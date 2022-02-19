Пример использования API и нативного нод-метода GET


const express = require("express");
const https = require("https"); 

const app = express();

app.get("/", function(req, res)
{
const url = "https://api.openweathermap.org/data/2.5/weather?q=Moscow&appid=483db3d642c24875f26393fe146c4492&units=metric"; 

https.get(url,function(response) 
{
    console.log(response.statusCode)

    response.on("data", function(data)
    {
    const weatherData = JSON.parse(data);
    const temp = weatherData.main.temp;
    const weatherDescription = weatherData.weather[0].description;
    const icon = weatherData.weather[0].icon;
    const imageURL = "http://openweathermap.org/img/wn/" + icon + "@2x.png";
    res.write("<p>The weather is " + weatherDescription + "</p>");
    res.write("<h1>Temperature is" + temp + "</h1>");
    res.write("<img src="+ imageURL +">");
    res.send();    
    })
})
});

app.listen(3000, function()
{
console.log("Server is on 3000");
}); 


* Чтобы вывести в консоль статус-код нужно
https.get(url,function(response) 
{
    console.log(response.statusCode);
})


*******

const express = require("express");
const https = require("https"); 
const bodyParser = require("body-parser"); 

const app = express();

app.use(bodyParser.urlencoded({extended: true}));

app.get("/", function(req, res)
{
    res.sendFile(__dirname + "/index.html");
});

app.post("/", function(req, res)
{
const query = req.body.cityName;
const APIKey = "483db3d642c24875f26393fe146c4492";
const unit = "metric"; 
const url = "https://api.openweathermap.org/data/2.5/weather?q=" + query + "&appid=" + APIKey + "&units=" + unit; 

https.get(url,function(response) 
{
console.log(response.statusCode);

    response.on("data", function(data)
    {
    const weatherData = JSON.parse(data);
    const temp = weatherData.main.temp;
    const weatherDescription = weatherData.weather[0].description;
    const icon = weatherData.weather[0].icon;
    const imageURL = "http://openweathermap.org/img/wn/" + icon + "@2x.png";
    res.write("<p>The weather is " + weatherDescription + "</p>");
    res.write("<h1>Temperature in" + query + "is " + temp + "</h1>");
    res.write("<img src=" + imageURL + ">");
    res.send();    
    });
});    
})

app.listen(3000, function()
{
console.log("Server is on localhost:3000");
}); 


***

*Для того, чтобы свойства стилей оставались при выгрузке на сервере также как и в локальных файлах 
следует использовать функцию express - static

app.use(express.static("public"));

* Далее создается директория в папке проекта public и в ней создается другая директория css и в нее помещается файл style.css и папка с файлами

* В файле html при необходимости актуализируются пути к перемещенным файлам, при это точка отсчета как если бы мы были уже в папке public

То есть

<link href="css/style.css" rel="stylesheet">

* Форма должна содержать следующие поля

<form action="/" class="form-signin" method="POST">

***
Для подписки используется к примеру 

https://mailchimp.com/

* Генерируется ключ.

* Находится ID листа.

* См. в документации. К примеру

Создается переменная в виде объекта и массив внутри - строка. Все это в app.post

var data = 
{
members: 
[{ 
email_adress: email,
status: "subscribed",
merge_fields: 
    {
    FNAME: FirstName,
    LNAME: LastName,
    }
}]
}

* Далее - переводится в формат JSON:

var jsonData = JSON.stringify(data);

***

Полный код:

app.post("/", function(req, res)
{
const FirstName = req.body.Name1;
const LastName = req.body.Name2;
const Email = req.body.Email;

const data = 
{
members: 
[{ 
email_adress: email,
status: "subscribed",
merge_fields: 
    {
    FNAME: FirstName,
    LNAME: LastName,
    }
}]
}

var jsonData = JSON.stringify(data);

console.log(FirstName, LastName, Email);
});

* Далее устанавливается метод https

const https = require("https");

* Под jsonData прописывается код

const url = "https://usX.api.mailchimp.com/3.0/lists/4061a48e5f";

// Где в конце - ID листа. Вместо Х следует подставить цифру из API ключа. 

const url = "https://us19.api.mailchimp.com/3.0/lists/4061a48e5f"; 
const options = 
{
method: "POST",
auth: "A-10:c66749b2c012fce8feebeb0e9e967ca7-us19",
}


https.request(url, options, function(response)
{
response.on("data", function()
{
    console.log(JSON.parse(data));
}
)
}
);

* Перед https.request создается новая переменная, которая 
будет содержать эти данные

const request = https.request(url, options, function(response)
{
response.on("data", function()
{
    console.log(JSON.parse(data));
}
)
}
);

* После этого новая переменная передаяется через

request.write(jsonData);

***
Итоговый полный код

const express = require("express");
const bodyParser = require("body-parser"); 
const request = require("request"); 
const https = require("https"); 

const app = express();

app.use(bodyParser.urlencoded({extended: true}));
app.use(express.static("public"));

app.get("/", function(req, res)
{
    res.sendFile(__dirname + "/signup.html");
});

app.post("/", function(req, res)
{
const FirstName = req.body.Name1;
const LastName = req.body.Name2;
const email = req.body.email;

const data = 
{
members: 
[{ 
email_address: email,
status: "subscribed",
merge_fields: 
    {
    FNAME: FirstName,
    LNAME: LastName,
    }
}]
};

const jsonData = JSON.stringify(data);

const url = "https://us19.api.mailchimp.com/3.0/lists/4061a48e5f"; 
const options = 
{
method: "POST",
auth: "A-10:c66749b2c012fce8feebeb0e9e967ca7-us19",
};

const request = https.request(url, options, function(response)
{
response.on("data", function(data)
{
    if (response.statusCode === 200)
    {
    res.sendFile(__dirname + "/sucess.html")
    }
    else
    {
    res.sendFile(__dirname + "/failure.html")
    }
})
});

request.write(jsonData);
request.end();
});    

app.post("/failure", function(req, res)
{
    req.redirect("/");
});

app.listen(3000, function()
{
console.log("Server is on localhost:3000");
}); 

// API 
// c66749b2c012fce8feebeb0e9e967ca7-us19

// List ID
// 4061a48e5f

*******
Heroku
*******

https://www.heroku.com/

* В терминале написать
$ heroku login

* Далее мэйл и пароль

* В коде заменить или добавить порт 
с 3000 на 

app.listen(process.env.PORT || 3000, function()
{
console.log("Server is on localhost:3000");
});

* В Директории проекта добавить файл

$ touch Procfile

* В созданном Procfile добавить код

web: node app.js

* Загружается в git

$ git init

$ git add .

$ git commit -m "1st commit"

* Далее создается новое приложение 

$ heroku create

* Далее - push

$ git push heroku master


*******
RESTful API
*******

* Подключение к robo 3t

* Запустить локально сервер mongod

* Сделать основу - см. файл
