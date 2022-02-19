*******
My SQL
*******

CRUD

- create
- read 
- update
- destroy

* ������ ��������

CREATE TABLE products (
id INT NOT NULL,
name STRING,
price MONEY,
PRIMARY KEY (id)
)

* ������ ���������� ��������

INSERT INTO products
VALUES (1, "Pen", 1.20)

���

INSERT INTO products VALUES (1, "Pen", 1.20)

* ����� ID �� ���� �������.

SELECT * FROM products WHERE id=1 

* ���������� �������� � �������, ����������� �����. 
������

UPDATE products
SET price = 0.80
WHERE id=2

* ���������� �������

ALTER TABLE products
ADD stock INT

* �������� ��������
DELETE FROM products
WHERE id=2

��� ������ ���������, �� ��� �� ����� ������ �������, 
WHERE name = "Pencil"

* ��������� ������� 
����� FOREIGN KEY

*******
MONGO DB
*******

* ������ 
$ mongod

� � ����� ���� 
$ mongo

* ����� ���������
$ help

* �������� ���� ������
$ use nameDB

* �������� ������� ���� ������ 
$ db

* ���������� ���������
$ db.name

* ���������� ���������� � ��������� (����� ���������� ����� � ��������� ���������)

$ db.name.insertOne({_id: 1, name: "Pen", price: 1.20})

* �������� ���������
$ show collections

* �������� ���������� ���������, ���� ������� ������ ��. ������������
$ db.collectioname.find()

� �������, ����� ���� �� �����
$ db.collectioname.find({name: "Pencil"})

��� ��� ���� ������ ��� 1
$ db.collectioname.find({price: {$gt: 1}})

* ������������ ������
$db.collectionname.updateOne({_id: 1}, {$set{stock: 32})

* �������� ������ 
$db.collectionname.deleteOne({_id: 2}) 

* ����������� ���������� � ������ ���������

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

��� ������ ������ ����������� - �������� ��������� ��������, ������������ ���������� � ������� ����� �������������

������:

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

* �������� ����
������� � ���� ���� ������ ����� use.

* �������� ������� 
db.dropDatabase()


*******
����������� MongoDb c Node.js 
*******

�������.

1) Native drive
2) ODM (Object document mapper): mongoose

*******
Mongoose
*******

* ���������
����� ������������� npm ���������� �����

$ npm i mongoose

� app.js

const mongoose = require("mongoose");

* ��� ��������� ����������
mongoose.connect("mongodb://localhost:27017/fruitsDB", { useNewUrlParser: true, useUnifiedTopology: true });

* ����� - ��������� ����� ��� ������������� ������

const schemaName = new mongoose.Schema ({
    name: String,
    rating: Number,
    review: String,

});

* ����� ��������� ������ - ��������� �� �����, � ������������ �����

const Fruit = mongoose.model("Fruit", fructSchema);

* �������� ��������� � ������-���������

const fruit = new Fruit
({
    name: "Apple",
    rating: 7,
    review: "Pretty solid as a friut",
    })

fruit.save();

* �������� � ���� ������ ��������� �������� � ������� + �������� ��� ������

modelName(���� ��� Fruit).insertMany([kiwi, orange, banana], function(err)
{ if (err) {console.log(err);}
  else {console.log("Ok"};  
}})

* ��������� � ������� � ��� ���������

modelName(� ������� Fruit).find(function (err, fruits){
{if (err) {console.log(err)}  
 else {console.log(fruits)};
}
});

* ������� ������ ������������ ���������� (� ������� - ���) + 
* ������� ����������

modelName(� ������� Fruit).find(function (err, fruits){
{if (err) {console.log(err)}  
 else 
 {
 
 mongoose.connection.close();       
 
 fruits.forEach(function(fruit)
    {
    console.log(fruit.name);
    };
}});

* ��������� ���������� ��������� � �����
������:

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

* ���������� ������

modelName(� ������� Fruit).updateOne({_id: 434958345934589}, {name: "Peach"},   function (err)
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

* �������� ������

modelName(� ������� Fruit).deleteOne({name: "Peach"}, function (err)
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

* ���������� ������

��� ���������� ������ �� ������ ����������, �� ����, ���������� ����������, ������� � �����, � ������� ����� ������� ������ �� ������ �����, ������� ������ �� ������� �� ������ �����.

const schemaName = new mongoose.Schema ({
    name: String,
    rating: Number,
    review: String,
    favoriteFruit: fruitSchema
});

��������, � ������� ��������� ������ � ������ ����� � 

const person = new Person 
({
    name: "Amy",
    age: "12,
    favoriteFruit: pineapple
})

����� - ���� � �����, �� ������� ������� ��������, ���������� ����� ��������:

const pineapple = new Fruit 
({
    name: "Pineapple",
    score: 9,
    review: "Great Fruit"
}),

�� �� ����� �������������� � ��������� person, ���� ������ ��� ���������� ��������.


*******
����� ����
*******

// DB Connection
mongoose.connect("mongodb://localhost:27017/todolistDB", { useNewUrlParser: true, useUnifiedTopology: true });

*******
���������� �� �������
*******

������������ �������� ������ Atlas 
