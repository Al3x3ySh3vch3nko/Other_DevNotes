������ ������������� API � ��������� ���-������ GET


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


* ����� ������� � ������� ������-��� �����
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

*��� ����, ����� �������� ������ ���������� ��� �������� �� ������� ����� ��� � � ��������� ������ 
������� ������������ ������� express - static

app.use(express.static("public"));

* ����� ��������� ���������� � ����� ������� public � � ��� ��������� ������ ���������� css � � ��� ���������� ���� style.css � ����� � �������

* � ����� html ��� ������������� ��������������� ���� � ������������ ������, ��� ��� ����� ������� ��� ���� �� �� ���� ��� � ����� public

�� ����

<link href="css/style.css" rel="stylesheet">

* ����� ������ ��������� ��������� ����

<form action="/" class="form-signin" method="POST">

***
��� �������� ������������ � ������� 

https://mailchimp.com/

* ������������ ����.

* ��������� ID �����.

* ��. � ������������. � �������

��������� ���������� � ���� ������� � ������ ������ - ������. ��� ��� � app.post

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

* ����� - ����������� � ������ JSON:

var jsonData = JSON.stringify(data);

***

������ ���:

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

* ����� ��������������� ����� https

const https = require("https");

* ��� jsonData ������������� ���

const url = "https://usX.api.mailchimp.com/3.0/lists/4061a48e5f";

// ��� � ����� - ID �����. ������ � ������� ���������� ����� �� API �����. 

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

* ����� https.request ��������� ����� ����������, ������� 
����� ��������� ��� ������

const request = https.request(url, options, function(response)
{
response.on("data", function()
{
    console.log(JSON.parse(data));
}
)
}
);

* ����� ����� ����� ���������� ����������� �����

request.write(jsonData);

***
�������� ������ ���

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

* � ��������� ��������
$ heroku login

* ����� ���� � ������

* � ���� �������� ��� �������� ���� 
� 3000 �� 

app.listen(process.env.PORT || 3000, function()
{
console.log("Server is on localhost:3000");
});

* � ���������� ������� �������� ����

$ touch Procfile

* � ��������� Procfile �������� ���

web: node app.js

* ����������� � git

$ git init

$ git add .

$ git commit -m "1st commit"

* ����� ��������� ����� ���������� 

$ heroku create

* ����� - push

$ git push heroku master


*******
RESTful API
*******

* ����������� � robo 3t

* ��������� �������� ������ mongod

* ������� ������ - ��. ����
