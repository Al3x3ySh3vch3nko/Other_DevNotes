�����������

https://habr.com/ru/company/hosting-cafe/blog/319710/

*******
Security
*******

������

1) ������� ����������� �� ���� ������

2) ����������. 

��� ����� 

$ npm i mongoose-encryption

��� ��������� �����

$ npm i dotenv

��������� ���� .env

� ���� ����������� ��������� ���������

const secret = "Thisisoursecret";

����������������� � ������

SECRET=Thisisoursecret

�������������� � ������������ ������


3) ����������� 

$ npm i md5

4) $ npm i bcrypt 

const bcrypt = require("bcrypt");
const saltRounds = 10;

const userSchema = new mongoose.Schema
({
    email: String,
    password: hash
});

app.post("/register", function(req, res)
{

    bcrypt.hash(req.body.username, saltRounds, function(err, hash)
    {
    const newUser = new User({
        email: req.body.username,
        password: md5(req.body.password)
    });

    newUser.save(function(err)
    {
        if (err) {console.log(err);}
        else{res.render("secrets");}
    });
});
});

*******
Hacking
*******

5)
*******
Cookies
*******

������ npm

express-session
passport
passport-local
passport-local-mongoose

6) 
*******
OAuth
*******
������������ npm ����� passport-google-oauth20 ��� ����� ������� ������ ��������� (��. ������������ passport)
