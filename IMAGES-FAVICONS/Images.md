1/ Удаление фона изображения нейросетью

https://www.remove.bg/

2/ Фильтры наложения нейросетями

https://www.ostagram.me/static_pages/lenta?last_days=1000&locale=en

https://deepart.io/#

3/ Через JS выделяет цвета, используемые на картинке

https://jariz.github.io/vibrant.js/

4. Создание фигуры в clip-path 
https://bennettfeely.com/clippy/

5. Обтекание текста https://developer.mozilla.org/en-US/docs/Tools/Page_Inspector/How_to/Edit_CSS_shapes

6. Как сохранить все картинки из PSD макета
https://www.youtube.com/watch?time_continue=3&v=1OdqlEUHF0o&feature=emb_logo


7. Из конференции---
Чтобы сделать описание svg-картинки для скринридеров следует
<img alt="Описание картинки"> 

8. Сохранение логотипов из Фотошопа
https://www.youtube.com/watch?v=1OdqlEUHF0o

9. Создание галереи.
Запрос функций.
Создается резервная разметка (инлайн), в нее встаривается:
@supports (display: grid) {
////
}

= 

<svg role="image" aria-label="Описание картинки">

---
Для добавления подписи к картинке следует использовать тэг figure для обертки 
и далее figcapture для описания.

---

Для часов.
использовать элементы контроля 

<input type="tel"> - дает выход на панель управления номера телефона, то есть на ввод символов и цифр

<input type="date"> - на выбор даты

<select> - выводит селектор

<itemprop> - объясняет разметку для часов и для режима чтения.

---

    @media(max-width: 1250px){
      min-width: 106%; 
      margin-top: 27px;}
    @media(max-width: 750px){
    }
    @media(max-width: 560px){
    }
    @media(max-width: 330px){
    }

====Подобрки баз изображений 
https://pikabu.ru/story/30_besplatnyikh_stok_resursov__chast_1_3998999
https://www.howtostartanllc.org/free-stock-photos/
---
http://www.coverr.co/#home
http://www.videvo.net/ (требуется упоминание автора)
http://www.lifeofvids.com/
http://www.videezy.com/ (Есть несколько лицензий. Смотрите сами нажав на имя автора напротив слова copyright)
http://www.wedistill.io/
https://morguefile.com/photos

12. Подбор цветов и оттенков
https://www.color-hex.com/

13. Сетка как в star citizen
background: url(/rsi/static/images/gridbg_glow.png) repeat center top;

14.
Анимация градиента

<figure>
    <a href="/">
        <img alt="Encycolorpedia" src="/082567-logo.svg">
    </a>
</figure>

animation: hue-rotate 6s linear infinite;

15. Прямая ссылка unsplash
Для unsplash есть интересный способ получить прямую ссылку на картинку, причем как на оригинал, так и на обрезанную.
Открываем страницу с фото
https://unsplash.com/photos/oRI7a2A6sno
Потом меняем url на этот
https://source.unsplash.com/oRI7a2A6sno
Если нужно обрезанное изображение, тогда добавляем еще слеш и размер
https://source.unsplash.com/oRI7a2A6sno/100x100


16. Хостинг фоток

https://photobucket.com/
