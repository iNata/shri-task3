ШРИ Задание №3 - Приложение
=======================================

Ссылка на исходный код: https://github.com/iNata/shri-task3

Ссылка на рабочий прототип: http://inata.github.io/shri-task3/client/

Выполнила: Андрейченко Наталья - natandreychenko@gmail.com


Комментарий по заданию
-----------------------

Описание процесса отладки: 

1. Склонировала код, после npm install выполнила npm start и открыла http://localhost:8080/. 
 В косоли браузера обнаружила сообщение об успешной регистрации http://joxi.ru/8An6Pk8fqEpoQA , Отключилась
 от сервера и посмотрела в консоль браузера http://joxi.ru/E2pdPyJIB0Laq2 и увидела сообщение об ошибках.
 
2. Прочитала, что ServiсeWorker используется для приложений с offline-функционалом, в частности для управления
кэшем ресурсов и результатов сетевых запросов. 

3. Зашла на chrome://flags, включила опцию enable-experimental-web-platform-features для просмотра информации
о текущий serviceWorker'ах. Убедила в том, что без подключения к серверу локально serviceWorker не активен.

4. Зашла во вкладку браузера resources, в раздел cache storage в список shri-2016-task3-1. В списке кэшируемых файлов 
все фалы были со статусом not found. Следовательно, так как приложение использует кэшируемые файлы, а их нет,
здесь корень ошибки.

5. Так как даже регистрация serviceWorker'a не проходила, ошибка заключалась в url-пути js-файла worker.js. 
 Ошибка могла возникнуть потому что локальная корневая структура отличается от серверной. Исправила url к скрипту
 и регистрация прошла. 
 
6. Исправила пути кэшируемых файлов в worker.js и они закэшировались в списке shri-2016-task3-1

7. Оставалась проблема, что url хранилища данных студентов был установлен всегда в директории api/v1/students/,
но без подключеия к серверу этой директории не существует. Соответственно для оффлайн режима нужно было напрямую
указать путь к файлу students.json.







 
