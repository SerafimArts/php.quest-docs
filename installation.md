## Как установить PHP?

> **Note**
> Обратите внимание, что данная инструкция предназначена для пользователей
> Windows OS, так как подавляющее большинство начинающих пользователей
> используют именно эту ОС.
>
> В том случае, если у вас например, Linux, то вряд ли материал на страницах
> этого сайта представляет какой-либо интерес в силу наличия опыта разработки.

Официальная сборка PHP доступна по адресу
[https://windows.php.net/download/](https://windows.php.net/download/).

> Старые версии PHP можно найти по адресу [https://windows.php.net/downloads/releases/archives/](https://windows.php.net/downloads/releases/archives/)

Если вы уже побежали открывать эту ссылку, то могли заметить, что на странице
содержится куча ссылок. Но не спешите пугаться, всё довольно просто!

## Сборки PHP

Для-начала, обратите внимание, что у каждой версии PHP (8.0, 8.1, 8.2 и т.д.)
есть 4 секции, которые озаглавливаются как:

- VS16 x64 Non Thread Safe
- VS16 x64 Thread Safe
- VS16 x86 Non Thread Safe
- VS16 x86 Thread Safe

В случае x64 и x86 всё довольно тривиально - это разные сборки под разную
платформу ОС. В том случае, если у вас 64-битная операционная система, то следует
использовать ссылки в разделе `x64`, если 32-битная, то соответсвенно `x86`.

Далее, следует определиться с выбором между "Thread Safe" (TS) и "Non Thread
Safe" (NTS). Тут тоже всё просто:
- TS сборка служит для работы в многопоточном режиме. Эту сборку следует
  выбирать в том случае, если вы собираетесь использовать Apache в режиме `mod_php`
  или расширения для работы с потоками (например устаревшее
  [pthreads](https://www.php.net/manual/en/book.pthreads.php)).
- NTS сборка служит для всех остальных целей.

> **Warning**
> В том случае, если вы не понимаете что написано выше, то просто выбирайте NTS.

Если подытожить, то список с описанием выглядит так:

- VS16 x64 Non Thread Safe - Для Windows x64
- VS16 x64 Thread Safe - Для Windows x64 с Apache в режиме mod_php
- VS16 x86 Non Thread Safe - Для Windows x86
- VS16 x86 Thread Safe - Для Windows x86 с Apache в режиме mod_php

Скорее всего у вас будет именно первый вариант ("VS16 x64 Non Thread Safe").

## Скачивание

Для того, чтобы скачать требуемую версию следует нажать на ссылку `Zip` на
странице.

![Ссылка на скачивание](/static/php-download.png)

После того, как скачается архив - вы можете распаковать его в любую директорию,
например: `C:/php/8.2/`.

Всё, теперь у вас есть PHP! Осталось его чуть-чуть настроить.

## Работа в Консоли

Теперь, для того, чтобы при введении слова `php` в консоли (в терминале)
запускался скачанный `php.exe` следует прописать его в переменной `PATH`.

Для этого следует нажать кнопки `Win` + `Pause Break`, а затем "Дополнительные
параметры системы". На Windows 11 это будет выглядеть следующим образом:

![Дополнительные параметры системы](/static/additional-properties.png)

После этого будет открыто окно "Свойства системы", в котором следует нажать на
кнопку "Переменные среды" (в самом низу окна):

![Переменные окружения](/static/env-variables.png)

В открывшемся окне будет два списка. Первый - набор переменных для текущего
пользователя, а второй - набор переменных для всех пользователей. Где именно
редактировать переменную - не принципиально.

Следует в этом списке найти переменную `Path` (учитывая регистр) и нажать на
кнопку "`Изменить`". В открывшемся окне нажимаем "`Создать`" и добавляем путь к
программе PHP. Результат может выглядеть следующим образом (в зависимости от того, 
куда был распакован PHP).

![Результат добавления в PATH](/static/env-variables-result.png)

После этого у нас появится возможность вводить любые команды, которые могут
выглядеть примерно так:

![Выполнение в консоли](/static/php-cmd.png)

Для этого просто откройте терминал и введите, например `php -v`.