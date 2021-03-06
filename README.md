# KeepSolid Assignment

Создано API библиотеки с использованием RDBMS Postgres и php фреймворка lumen.
Локальное окружение поднято с помощью Docker Compose.

## Авторизация

Для регистрации использовать POST запрос к /users/registry и телом запроса login='email',password='password'.

Для аутентификации использовать POST запрос к /users/login и телом запроса login='email',password='password'.

Для выхода из учётной записи использовать POST запрос к /users/logout.

## Книги

### Гость (не требует логин)

#### Для получения всех доступных книг использовать GET запросы к :

-   /books/get/ - получение базовой информации по всем книгам;
-   /books/get/genres - получение книг и их жанров;
-   /books/get/authors - получение книг и их авторов;
-   /books/get/all - получение книг, их жанров и авторов;

Для получения информации по отдельной книге использовать GET запросы для всех доступных книг, с добавлением id книги
Пример:
/books/get/1

Так же можно посмотреть все доступные жанры и авторов GET запросами:

-   /genres/get
-   /authors/get

Или конкретные жанры по аналогии с книгами:

-   /genres/get/1
-   /authors/get/1

### Пользователь

#### Добавление книги в избранное пользователем:

Post запрос к /users/add_to_favorite
В теле запроса указать book_id требуемой книги.

#### Удаление книги из избранного:

Delete запрос к /users/remove_from_favorite
В теле запроса указать book_id требуемой книги.

### Администратор

#### Добавление новой книги:

Post запрос к /books/add с телом запроса
title='Название книги', descr='Описание книги'

Так же есть возможность добавить новый жанр и автора Post запросами:

-   /genres/add, Тело: title='Название жанра', descr='Описание жанра'
-   /authors/add, Тело: first_name='Имя', last_name='Фамилия', descr='Описание автора'

Кроме этого можно добавить книге автора или жанр Post запросами:

-   /books/add_genre/{id}, где id - id книги и телом запроса: genre_id=...
-   /books/add_author/{id}, где id - id книги и телом запроса: author_id=...

#### Удаление книги:

Delete запрос к /books/drop/{id}, где id - id книги.

Аналогично можно удалить жанр и автора обращаясь к

-   /genres/drop/{id}, где id - id жанра.
-   /authors/drop/{id}, где id - id автора.

И удалить жанр или автора конкретной книги:

-   /books/drop_genre/{id}, где id - id книги, а в теле запроса указывать genre_id=...
-   /books/drop_author/{id}, где id - id книги, а в теле запроса указывать author_id=...

#### Скачать csv файл

Get запрос к:

-   /books/download для скачивания списка книг в формате .csv;
-   /books/download/genres для скачивания списка книг и их жанров в формате .csv;
-   /books/download/authors для скачивания списка книг и их авторов в формате .csv;
-   /books/download/all для скачивания списка книг, их жанров и авторов в формате .csv;

## Роли

Для изменения роли пользователя используется команда:

php artisan setrole -R [user/admin] [Идентификатор пользователя]

## Диаграммы

В каталоге /diagram представлены:

-   ER Diagram базы данных
-   Class Diagram проекта
-   Sequence Diagram для процессов аутентификации и авторизации (Sequence Diagram)
-   Sequence Diagram для POST, GET и DELETE запросов к библиотеке (Sequence Diagram Library)

## Обратная связь

-   GMAIL: mykhailo.zhar@stud.onu.edu.ua
-   Telegram: @IHATEB335
