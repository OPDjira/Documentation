

# Запросы

  

## Оглавление

+ [login](#login)
+ [booking](#booking)

  
  

## /login/

Запрос для проверки валидности введенных юзером данных

  

### Входные данные

+ **email**  *(String)* - Почта из поля *username*
+ **password**  *(String)* - Пароль

 ### Возврат ответа
 Бекэнд возвращает два статуса: (404 и пустое тело запроса, если пользователь не найден и 200, если пользователь существует) 
 При **успешном** запросе сервер вернет объект пользователя из базы данных, сериализованный в JSON формат:
 ~~~
{
    "username": "John Doe",
    "password": "12345",
    "email": "johndoe@spbstu.ru",
    "access": "Student"
}
~~~
 

### Пример запроса:
#### Запрос:
~~~
Method: Post
Address: http://127.0.0.1:8000/login/
Headers
{  
    'Accept': 'application/json, text/plain, */*',  
    'Content-Type': 'application/json',  
},
Payload
{
	username: "johndoe@spbstu.ru",
	password: "12345"
}
~~~
#### Ответ будет выглядеть как:
 ~~~
{
    "username": "John Doe",
    "password": "12345",
    "email": "johndoe@spbstu.ru",
    "access": "Student"
}
~~~

## /booking/

**GET Запрос:** получает JSON с занятыми аудиториями 

  ### Входные данные

+ **building**  *(Integer)* - ID корпуса *building_id*
+ **date**  *(Date)* - Дата брони
+ **time**  *(Time)* - Время брони

 ### Возврат ответа
 Бекэнд возвращает JSON со списком с бронями
 При **успешном** запросе сервер вернет список с объектами брони из базы данных, сериализованный в JSON формат:
 ~~~
{
	"bookings":  [
			{
			"audience":  1033,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  563,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  532,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  554,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  1304,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  1358,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			}
		]
}
~~~
 

### Пример запроса:
#### Запрос:
~~~
Method: GET
Address: http://127.0.0.1:8000/booking/
Headers
{  
    'Accept': 'application/json, text/plain, */*',  
    'Content-Type': 'application/json',  
},
Payload
{
"building":  "11",
"date":  "2024-05-04",
"time":  "16:00:00"
}
~~~
#### Ответ будет выглядеть как:
 ~~~
{
	"bookings":  [
			{
			"audience":  1033,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  563,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  532,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  554,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  1304,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			},
			{
			"audience":  1358,
			"time":  "16:00:00",
			"date":  "2024-05-04",
			"ordered_by":  null
			}
		]
}
~~~
**GET Запрос:** занимает аудиторию и выдает JSON с данными о броне

### Входные данные

+ **building**  *(Integer)* - ID корпуса *building_id*
+ **audience**  *(Integer)* - ID аудитории *audience_id*
+ **date**  *(Date)* - Дата брони
+ **time**  *(Time)* - Время брони
+ **student** *(String)* - email студента *student_email*

 ### Возврат ответа
 Бекэнд возвращает JSON с данными брони/ошибкой

### Пример запроса:
#### Запрос:
~~~
Method: POST
Address: http://127.0.0.1:8000/booking/
Headers
{  
    'Accept': 'application/json, text/plain, */*',  
    'Content-Type': 'application/json',  
},
Payload
{
{
    "building": 11,
    "audience": 528,
    "date": "2024-05-11",
    "time": "22:00:00",
    "email": "test@mail.com"
}
}
~~~
#### Ответ будет выглядеть как:
 ~~~
{
	"audience": 528,
	"time": "22:00:00",
	"date": "2024-05-11",
	"ordered_by": 1
}
~~~
 
>Feel free to add your stuff here!
