***
Инструменты
***

https://habr.com/ru/company/hosting-cafe/blog/319710/

***
## Security
***

Уровни

1. Простая регистрация по базе данных

2. Шифрование. 

или Пакет 

`$ npm i mongoose-encryption`

или Переменые среды

`$ npm i dotenv`

Создается файл .env

В него вставляется шифруемое сообщение

`const secret = "Thisisoursecret";`

Переформатируется в формат

`SECRET=Thisisoursecret`

Форматирование в документации пакета

3. Хеширование 

`$ npm i md5`

4. `$ npm i bcrypt` 
```
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
```

*******
Cookies
*******

Модули npm

express-session
passport
passport-local
passport-local-mongoose

*******
OAuth
*******
Использовать npm пакет passport-google-oauth20 или более позднюю версию стратегии (см. документацию passport)
