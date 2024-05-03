
# Запросы

  

## Оглавление

+ [login](#login)

  
  

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
 
>Feel free to add your stuff here!
