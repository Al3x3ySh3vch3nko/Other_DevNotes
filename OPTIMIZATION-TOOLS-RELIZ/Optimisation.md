***
#### Элементы ускорения загрузки
***

1. Использовать сборщики

2. Проверять валидаторами
https://validator.w3.org
https://jigsaw.w3.org/css-validator/

3.Проверять выгруженные сайты через 
https://developers.google.com/speed/pagespeed/insights/

4. Сжимать изображения и код:
png и jpeg https://tinypng.com
svg https://jakearchibald.github.io/svgomg/
css https://csscompressor.com
js https://jscompress.com  

Для установки стратегии загрузки шрифтов сначала базовые - потом дизайнерские в файле fonts (fonts.min.css) следует в начале кода после @font-face добавить 

    font-display: swap;
    
А в файле с подключением шрифтов указывать несколько шрифтов для загрузки.

Стартегии загрузки:

https://webformyself.com/css-font-display-budushhee-rendera-shriftov-v-vebe/

5. Кэшировать информацию

6. Ускорение работы 
https://webo.in/articles/habrahabr/15-yahoo-best-practices/#cdn

7. Ускорение прокрутки отключением hover.
https://habr.com/ru/post/204238/

8. Mobile friendly test
https://search.google.com/test/mobile-friendly?utm_source=support.google.com%2Fwebmasters%2F&utm_medium=referral&utm_campaign=%206352293


***
#### Инструменты
***
https://astro.build/ - новый инструмент, исключающий в финальной версии JS и содержащий я иных оптимизаций. По данным разработчиков заметно ускоряет работу
