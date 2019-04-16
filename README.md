Тестовое задание Java Backed Developer
======================================

Необходимо разработать REST-сервис на базе Spring Framework (можно Spring Boot)
для получения курса иностранной валюты к рублю. В качестве источника данных следует
использовать ресурс [ЦБ России](http://www.cbr.ru/scripts/Root.asp).

Выбор библиотек и все допущения остаются на усмотрение разработчика.

Результат выполения задания должен содержать в себе исходный код приложения, 
а также инструкцию по сборке и запуску. Решение небходимо разместить на 
[гитхабе](https://github.com/) и отправить ссылку на почту [feedback@null-pointer.ru](mailto:feedback@null-pointer.ru).


API Приложения
--------------

### Запрос

    GET /api/rate/{code}/{date}


### Параметры

* code [строка 3 символа, обязателен] - трехсимвольный код валюты
* date [дата в формате yyyy-MM-dd, строка, опционален] - дата актуальности курса

Если в запросе не указана дата актуальности курса, то такой датой считается
следующий день от текущей даты осуществления запроса.

### Ответ

```json
{
    "code": "<Код валюты>",
    "rate": "<Курс>",
    "date": "<Дата актуальности>"
}
```

Ответ содержит следующие поля:

* code [строка 3 символа, обязателен] - трехсимвольный код валюты
* rate [десятичное число, строка, обязателен] - курс валюты
* date [дата в формате yyyy-MM-dd, строка, обязателен] - дата актуальности курса


### Примеры запросов

    GET http://example.com/currency/api/rate/USD

    GET http://example.com/currency/api/rate/USD/2015-09-24


### Пример ответа

```json
{
    "code": "USD",
    "rate": "66.0410",
    "date": "2015-09-24"
}
```

Курс доллара США на 24 сентября 2015 года составляет 66 рублей и 4,1 копейки.
