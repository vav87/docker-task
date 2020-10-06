# Задание
Есть два Spring-boot сервиса: 
* **admin-server** - сервис-"админ", агрегирующий информацию о состоянии сервисов-"клиентов", 
которые исполняют какую-либо бизнес-логику. Под капотом использует _spring-boot-admin_ Инфа тут: https://github.com/codecentric/spring-boot-admin
* **client-service** - некое бизнес приложение, которое может работать с сущностью пользователь(User). 

`client-service` Имеет 2 контроллера и 2 endpoint'a в каждом из них. 
Если запустить его просто локально с профилем `dev` (см. _application.properties_):

`gradlew bootRun` то он использует следующие эндпоинты:

```
POST /mock/user/create HTTP/1.1
Host: localhost:8080
Content-Type: application/json

{
    "firstName": "Example",
    "lastName": "Example"
}

GET /mock/user/{createdID} HTTP/1.1
Host: localhost:8080

```
и сохраняет все данные в Hashmap.

Но если запустить его с профилем `prod`, то приложение будет использовать для сохранения данных **MongoDB** и другие эндпоинты:
```
POST /user/create HTTP/1.1
Host: localhost:8080
Content-Type: application/json

{
    "firstName": "Example",
    "lastName": "Example"
}

GET /user/{createdID} HTTP/1.1
Host: localhost:8080

```
### Задача 1 (минимум)
Сделать докер-образы обоих сервисов: `admin-server`, `client-service`(с профилем dev). Запушить образы в **dockerHub**. 
Связать их друг с другом в одном docker-compose файле и сделать pull-request в репозиторий. 
### Задача 2 (стандарт)
Установить в `client-service` профиль `prod`. Заменить настройки в `application-prod.properties` согласно тем, что нужны вам. 
Подключить через docker-compose дополнительно `mongodb` и `mongo-express` 
Настроить приложения так, чтобы они работали в связке и сущности пользователей сохранялись в mongo, а не локальную мапу.
### Задача 3 (отлично)
Вынести все настраиваемые параметры в `env` переменные или файлы, чтобы их можно было конфигурировать самостоятельно, 
а не только использовать те, что зашиты в `application.properties`

# Дедлайн
**18.10.2020 23:59 GMT+3**