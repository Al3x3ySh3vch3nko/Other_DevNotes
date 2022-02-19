*******
My SQL
*******

CRUD

- create
- read 
- update
- destroy

* Пример создания

CREATE TABLE products (
id INT NOT NULL,
name STRING,
price MONEY,
PRIMARY KEY (id)
)

* Пример добавления значений

INSERT INTO products
VALUES (1, "Pen", 1.20)

или

INSERT INTO products VALUES (1, "Pen", 1.20)

* Выбор ID во всей таблице.

SELECT * FROM products WHERE id=1 

* Добавление величины в таблицу, заполненную ранее. 
Пример

UPDATE products
SET price = 0.80
WHERE id=2

* Добавление столбца

ALTER TABLE products
ADD stock INT

* Удаление величины
DELETE FROM products
WHERE id=2

или вместо последней, но это не самый точный вариант, 
WHERE name = "Pencil"

* Связывать таблицы 
через FOREIGN KEY

*******
MONGO DB
*******

* Запуск 
$ mongod

и в новом окне 
$ mongo

* Вызов помощника
$ help

* Создание базы данных
$ use nameDB

* Проверка текущей базы данных 
$ db

* Добавление коллекции
$ db.name

* Добавление информации в коллекцию (можно совместить сразу с созданием коллекции)

$ db.name.insertOne({_id: 1, name: "Pen", price: 1.20})

* Просмотр коллекций
$ show collections

* Показать содержимое коллекции, есть фильтры поиска см. документацию
$ db.collectioname.find()

К примеру, поиск всех по имени
$ db.collectioname.find({name: "Pencil"})

Или где цена больше чем 1
$ db.collectioname.find({price: {$gt: 1}})

* Перезаписать данные
$db.collectionname.updateOne({_id: 1}, {$set{stock: 32})

* Удаление данных 
$db.collectionname.deleteOne({_id: 2}) 

* Объединение документов в рамках коллекции

db.products.insert(
{
_id: 3,
name: "Rubber:,
price: 1.30,
stock: 43, 
reviews: [
    {
        authorName: "Sally",
        rating: 5, 
        review: "Best rubber ever!"
    },
    {
        authorName: "John",
        rating: 5, 
        review: "Awesome rubber!"
    }
        ]
}
)

ИЛИ другой способ объединения - создание отдельных объектов, объединенных коллекцией в массиве через идентификатор

Пример:

{
_id: 1,
name: "Pen",
price: 1.20,
stock: 32
}

{
_id: 2,
name: "Pencil",
price: 0.80,
stock: 12
}

{
orderNumber: 3243,
productOrder: [1, 2]
}

* Удаление базы
перейти к этой базе данных через use.

* Написать команду 
db.dropDatabase()


*******
Объединение MongoDb c Node.js 
*******

Способы.

1) Native drive
2) ODM (Object document mapper): mongoose

*******
Mongoose
*******

* Установка
после инициализации npm установить пакет

$ npm i mongoose

В app.js

const mongoose = require("mongoose");

* Для установки соединения
mongoose.connect("mongodb://localhost:27017/fruitsDB", { useNewUrlParser: true, useUnifiedTopology: true });

* Далее - создается схема для представления данных

const schemaName = new mongoose.Schema ({
    name: String,
    rating: Number,
    review: String,

});

* Далее создается модель - коллекция по схеме, в единственном числе

const Fruit = mongoose.model("Fruit", fructSchema);

* Создание документа в моделе-коллекции

const fruit = new Fruit
({
    name: "Apple",
    rating: 7,
    review: "Pretty solid as a friut",
    })

fruit.save();

* Добавить в базу данных несколько объектов в массиве + добавить лог ошибок

modelName(выше это Fruit).insertMany([kiwi, orange, banana], function(err)
{ if (err) {console.log(err);}
  else {console.log("Ok"};  
}})

* Прочитать и вывести в лог коллекцию

modelName(в примере Fruit).find(function (err, fruits){
{if (err) {console.log(err)}  
 else {console.log(fruits)};
}
});

* Вывести только определенную информацию (в примере - имя) + 
* Закрыть соединение

modelName(в примере Fruit).find(function (err, fruits){
{if (err) {console.log(err)}  
 else 
 {
 
 mongoose.connection.close();       
 
 fruits.forEach(function(fruit)
    {
    console.log(fruit.name);
    };
}});

* Валидация параметров документа в схеме
Пример:

const schemaName = new mongoose.Schema ({
    name: String,
    rating: 
    {
        type: Number,
        min: 1,
        max: 10
    },    
    review: String,
});

* Обновление данных

modelName(в примере Fruit).updateOne({_id: 434958345934589}, {name: "Peach"},   function (err)
{
if (err) 
{
console.log(err);
}
else 
{
console.log("Ok");
}
});

* Удаление данных

modelName(в примере Fruit).deleteOne({name: "Peach"}, function (err)
{
if (err) 
{
console.log(err);
}
else 
{
console.log("Ok");
}
});

* Связывание данных

Для добавления данных из других документов, то есть, связывания документов, следует в схеме, в которую нужно вносить данные из другой схемы, сделать запись со ссылкой на другую схему.

const schemaName = new mongoose.Schema ({
    name: String,
    rating: Number,
    review: String,
    favoriteFruit: fruitSchema
});

Документ, в который заносятся данные с учетом схемы и 

const person = new Person 
({
    name: "Amy",
    age: "12,
    favoriteFruit: pineapple
})

Далее - если в схеме, из которой берется документ, существует такой документ:

const pineapple = new Fruit 
({
    name: "Pineapple",
    score: 9,
    review: "Great Fruit"
}),

То он будет использоваться в документе person, куда войдет как включенный документ.


*******
Блоки кода
*******

// DB Connection
mongoose.connect("mongodb://localhost:27017/todolistDB", { useNewUrlParser: true, useUnifiedTopology: true });

*******
Размещение на сервере
*******

Использовать нативный сервер Atlas 
