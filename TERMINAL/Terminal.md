*******
1.Проверка установки GitBash в Hyper.
*******

`$ echo $Shell`

Должен показать bin/bash/

*******
2.Команды
*******

* `pwd`
(print working directory)
Показывает текущую директорию

* `ls`
(List)
Показывает файлы в текущей папке

* `ls * .txt`
Выводит все файлы в директории с расширением .txt

* `ls -l`
Подробная форма списка

* `ls -rtl`
Формирует список с сортировкой от последних измененных

* `ls -a`
Показывает все файлы, в том числе скрытые

* `.NewText3.txt`
Скрытый файл

* `cdт`
(Change Directory)
Меняет директорию

* `TAB` - автозаполнение слова при написании директории

* `cd ~`
Вернуться в корневую директорию

* `cd Documents/Code/Test Area`
Пример ввода полного пути к файлу

* `cd ..`
Назад на 1 уровень

* `Удерживая Alt`
Дает возможность использовать курсор

* `Ctr + A`
Переместиться в начало строки

* `Ctrl + E`
Переместиться в конец строки

* `Сtrl + U`
Очистить линию

* `Ctrl + C`
Сбрасывет текущую команду (при зависании и пр.)

* `mkdir`
mkdir NewFolder
(Make Directory)
Создание новой директории

* `mv`
(Move)
mv test test.txt
Переименование файла test в test.txt

* `cp`
(Copy)
cp test.txt
Копирование файла

* `touch` 
touch text2.txt
Создание нового файла

* `open`
open text2.txt
Открытие файла

* `open -a` 
open -a Atom text2.txt
Открытие файла через конкретное приложение

* `rm`
rm text2.txt
(Remove)
Удаление файла

* `rm *`  
Удаление всех файлов в директории

* `rm -r`
rm -r Documents/
Удаление директории

* `Сtrl + L`
Очистка терминала

* `clear`
Очистка терминала

* `Ctrl + D`
Выход из терминала

* `echo "Пример текста" > NewText2.txt`
Создает строку "Пример текста" в файле NewText2.txt, заменяя ранее набранную

* `echo "Пример текста2" >> NewText2.txt`
Создает новую строку "Пример текста2" и добавляет ее в конец файла NewText2.txt, не заменяя ранее набранную

* `cat NewText2.txt`
(Сoncatenate)
Выводит содержимое из файла NewText2.txt

* `diff` 
Сравнение
diff NewText.txt NewText2.txt
Сравнение содержимого файлов
