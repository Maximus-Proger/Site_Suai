## Site_Suai
____
## Цель работы:
Спроектировать и разработать систему авторизации пользователей на протокоде HTTP
## Реализованные возможности
+ функциональность входа/выхода
+ хранение паролей в хешированном виде
+ форма регистрации
+ смена пароля
+ восстановление пароля
+ ограниичение времени сессии
+ валидация пароля
+ хранение хеша пароля с солью
____
<<<<<<< HEAD
## Ход работы
### 1. Разработка пользовательского интерфейса
В ходе выполнения работы был разработан пользовательский интерфейс при помощи графического редактора [Figma](https://www.figma.com/community)

+ Интерфейс главной страници для неавторизованных пользователей и страница авторизации

![figma1](https://user-images.githubusercontent.com/98755619/197325213-f7bfa644-b26f-4726-a218-2e9ceb341bfb.png)
----
+ Интерфейс страницы регистрации и страницы сброса пароля

![figma2](https://user-images.githubusercontent.com/98755619/197325224-510c3fa4-1182-4231-a11f-0868f5b3cd14.png)
----
+ Интерфейс главной страницы для авторизированных пользователей и страницы смены пароля
 
![figma3](https://user-images.githubusercontent.com/98755619/197325258-312f5316-a61e-47c8-b99d-0395ea0a6b93.png)

### 2. Описание пользовательских сценариев работы
+ #### Сценарий регистрации
1) Пользователь заходит на сайт и попадает на главную страничку, на которой нажимает кнопку "Зарегистрироваться",
после этого клиента перекидывает на страничку регистрации.
2) Клиент должен заполнить все поля и при успешном заполнении отправить форму, в противном случае будет выпадать ошибка
регистрации с указанием проблемы.
3) После этого пользователя перекинет на основную страничку сайта.
+ #### Сценарий входа
1) Пользователь заходит на сайт и попадает на главную страничку, Если пользователь уже зарегистрирован на сайте,
то он может нажать на кнопку "Войти", после этого клиента перекидывает на страничку входа.
2) Клиент должен заполнить поля данными, которые он указывал при регистрации, и при успешном заполнении отправить форму,
в противном случае будет выпадать ошибка входа.
3) После успешного входа пользователя перекинет на основную страничку сайта.
+ #### Сценарий восстановления пароля
1) Пользователь заходит на сайт и попадает на главную страничку, если пользователь уже зарегистрирован на сайте,
но забыл пароль, то он может нажать на кнопку "Забыли пароль?", после этого клиента перекидывает на страничку
восстановления пароля.
2) Клиент должен указать адрес электронной почты, который он указывал при регистрации, после этого ему на почту придёт
письмо с дальнейшими инструкциями
3) Пользователь должен открыть письмо и перейти по ссылке в нём, после этого его перекинет на страничку ввода
нового пароля
4) После заполнения полей по смене пароля пользователь сможет зайти на сайт по новому паролю
+ #### Сценарий смены пароля
1) Пользователь заходит на сайт и попадает на главную страничку, после этого заходит в свой аккаунт.
2) Если Пользователь хочет сменить пароль, то ему требуется нажать на кнопку "Сменить пароль?", после этого клиента
перекидывает на страничку изменения пароля.
3) Клиент должен заполнить поля связанные со старым и новым паролями, затем при успешном заполнении отправить форму,
в противном случае будет выпадать ошибка смены пароля.
4) После этого пользователь сможет заходить в свой аккаунт под новым паролем.
### 3. Описание API сервера и хореографии

+ Пример запросов, когда пользователь проходит процесс регистрации на сайте

![SignUp](https://user-images.githubusercontent.com/98755619/197325433-e49c679b-2351-4b45-afc7-232e84fa79a4.png)
----
+ Пример запросов, когда пользователь проходит процесс авторизации на сайте

![login](https://user-images.githubusercontent.com/98755619/197325502-30deff0e-77b4-40ae-ab5d-66da2cf0031d.png)
----
+ Пример запросов, когда пользователь проходит процесс сброса пароля на сайте

![PasswordReset](https://user-images.githubusercontent.com/98755619/197325534-9706cdce-40e6-4ea0-a173-ce4d92e7d65e.png)
----
+ Пример запросов, когда пользователь проходит процесс смены пароля на сайте

![PasswordChange](https://user-images.githubusercontent.com/98755619/197325553-df61ed4b-6b57-4d97-85ab-f597cad1febd.png)

### 4. Описание структура базы данных

Для хранения данных использовалась встраиваемая кроссплатформенная БД - SQLite

Пример хранения данных пользователя Max:

| id           | password                               | last_login                 | username | first_name | email       | is_active | date_joined                |
|--------------|----------------------------------------|----------------------------|----------|------------|-------------|-----------|----------------------------|
| 1            | pbkdf2_sha256$15..0$3..D$op1..p7/Wh..Q | 2022-10-17 16:47:26.099217 | Max      | Maxim      | Max@mail.ru | 1         | 2022-10-04 18:19:32.425677 |

### 5. Описание алгоритмов 
+ Алгоритм действий пользователя при регистрации на сайте

![SignUp_block drawio](https://user-images.githubusercontent.com/98755619/197325617-2afea13d-ddcd-4fe7-b16a-30d4859d739a.png)
----

+ Алгоритм действий пользователя про авторизации на сайте

![login drawio](https://user-images.githubusercontent.com/98755619/197325649-d07eb42b-16d9-4ae7-8e8a-8d244a5dfc80.png)

### 6. Значимые фрагменты кода



