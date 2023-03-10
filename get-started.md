> **Warning**
> Эта страница является копипастой информации с сайта [http://phpfaq.ru/](http://phpfaq.ru/),
> она ОЧЕНЬ СИЛЬНО устарела и требует обновления. Пожалуйста, пока что просто
> проигнорируйте её. Данная информация скорее всего больше навредит, нежели
> как-то поможет.

## Информация для начинающих изучать PHP и MySQL

Для тех, кто хочет изучать PHP, можно посоветовать великолепный "Самоучитель PHP" с сайта PHP5.RU
Курс находится в процессе написания, но уже сейчас ссылки на отдельные уроки из него стоят в различных разделах этого FAQ. И, поверьте - оно стоит того.
Не могу не порекомендовать замечательный материал Вадима Ткаченко АКА Bizon-а "Вступление в PHP и MySQL". Он даже издавался отдельной книгой, а сейчас - исправленный и дополненный - размещается на сайте
"PHP в деталях". Этот ресурс стоит особняком. В отличие от предыдущих, рекомендовать прочесть его целиком может только садист - там слишком много информации. но в этом и его прелесть. Это неисчерпаемый ресурс информации по PHP. Единственное замечание - обращайте внимание на дату написания статьи. Не стоит особо доверять тем, что написаны до 2003 года.
Ну, и, конечно же - этот сайт, http://phpfaq.ru
Если вы еще не прочли его целиком - обязательно сделайте это. Здесь перечислены проблемы, с которыми рано или поздно столкнется КАЖДЫЙ, кто пишет на PHP.

## Программное обеспечение.

Для работы с РНР под Windows, надо установить следующие программы:
- web-сервер Apache (5Mb)
- сам PHP (10Mb)
- по желанию - MySQL (23Mb).

Настройка очень простая. Апач устанавливается программой установки. Там, где он запрашивает имя вашего сервера и емейл администратора, надо 2 раза написать `localhost` и свой e-mail.
PHP распаковывается из зипа в любой каталог по желанию (стандартно - `C:\PHP`) и настраивается обязательно как модуль Апача. Для этого надо выполнить три действия:

- переписать файл php5ts.dll в каталог WINDOWS
- в файл httpd.conf (C:\Program Files\Apache Group\Apache\conf\httpd.conf), в самом низу, добавить две строчки

```
LoadModule php5_module c:/php/php5apache2_2.dll
AddType application/x-httpd-php .php .phtml
```
- перезапустить Апач (с помощью утилиты Apache monitor в трее)

Выполнив все эти действия, можно положить тестовый php скрипт (допустим, он называется `test.php` и состоит из строчки
`<?php phpinfo(); ?>`
в каталог, который является корневым для веб-сервера (по умолчанию это `C:\Program Files\Apache Group\Apache\htdocs\`) и обратиться к нему, написав в браузере адрес `http://127.0.0.1/test.php`

При установке MySQL выбрать Standard configuration, на следующем экране нажать Next, на следующем - задать пароль или снять галочку "Modify security settings", если хотите оставить его пустым.

Для проверки запустите консоль Mysql:
- Пуск - Выполнить и в появившуюся строку скопировать
  `"C:\Program Files\MySQL\MySQL Server 5.1\bin\mysql.exe"`
  или
  `"C:\Program Files\MySQL\MySQL Server 5.1\bin\mysql.exe" -uroot -pPASSWORD`

Eсли консоль запустилась - все работает. Наберите `exit` для выхода и приступайте к конфигурированию поддержки mysql в PHP.
Для этого, если вы не сделали этого раньше, возьмите файл `C:\php\php.ini-development` и скопируйте под именем `php.ini` в каталог windows. Затем отредактируйте его, убрав точку с запятой в начале строки
`;extension=php_mysql.dll`
и отредактировав параметр `extension_dir`:
`extension_dir = "c:\php\ext\"`
заодно можно сразу исправить
`short_open_tag = On`
чтобы работали старые скрипты и удобные шаблоны
и не забудьте после этого перезапустить Апач, как это было описано выше.
Теперь вы можете использовать mysql в своих php-скриптах.

Те, для кого эта инструкция слишком сложна, могут попробовать установить готовый комплект Денвер-2.
В него входит сразу все, что нужно, и еще много ненужного. А главное - работает все само.
Еще одно достоинство Денвера в том, что объем базового комплекта в 10 раз меньше полных версий - всего 4 мегабайта. А так же то, что его автор пишет интересные книжки по PHP.

Так же, всем любознательным рекомендуется ВЕСЬМА толковая статья Установка и настройка Apache+PHP
с сайта PHP5.RU. И, конечно же - разделы официальной документации, посвященные установке соответствующих программ.

## Форумы.

При изучении любого дела обязательно появятся вопросы.
Вопросы удобно задавать на форумах.
[Форум PHPклуба](http://phpclub.ru/talk/forumdisplay.php?s=&forumid=12). Самый посещаемый и известный. К сожалению, известность служит ему дурную службу. Очень часто на вопрос новичка отвечает еще более зеленый новичок, давая совершенно неправильный ответ. Однако профессионалов там тоже предостаточно, готовых объяснить ошибки и первому и второму.

PHP представлен и в русскоязычном сегменте Livejournal
В сообществах ru_php и [info]ru_mysql всегда найдутся профессионалы, кототорые помогут с любой проблемой. Только не забудьте сначала прочитать правила сообщества!

Задавая вопрос на форуме, помните:
Что, скорее всего, с ним уже сталкивалась тыща человек. И подробные ответы можно найти в поиске. Если же, все-таки, вопрос приходится задавать - то описывайте как можно подробнее (только своими словами, а не кодом!), что вы делали, что хотели получить и что получилось в результате, а так же точно копируйте сообщения об ошибках.

## Сайты для начинающих.

Ранее здесь были размещены ссылки на различные сайты от начинающих для начинающих.
К сожалению, и так-то не блиставшие качеством материала, они давно заброшены своими авторами и окончательно потеряли актуальность.
Все, что есть лучшего по теме PHP, перечислено вверху страницы.
Если вы знаете хороший сайт - напишите о нем в разделе "Обратная связь".
