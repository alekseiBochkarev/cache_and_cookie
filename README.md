# cache_and_cookie

Пример кода для кэша и куки:

Пример использования кэша:

HTML (index.html):
```HTML
<!DOCTYPE html>
<html>
<head>
    <title>Пример кэша</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <h1>Пример кэширования</h1>
    <img src="image.png" alt="Example Image">
</body>
</html>
```

CSS (styles.css):
```CSS
body {
    font-family: Arial, sans-serif;
}

h1 {
    color: blue;
}
```

Заголовки HTTP (при ответе сервера):
```http
HTTP/1.1 200 OK
Cache-Control: max-age=3600
ETag: "abcdef12345"
```
Пример использования куки:

HTML (index.html):
```HTML
<!DOCTYPE html>
<html>
<head>
    <title>Пример куки</title>
</head>
<body>
    <h1>Пример использования куки</h1>
    <button onclick="setCookie('username', 'JohnDoe', 7)">Сохранить имя пользователя</button>
    <button onclick="alert(getCookie('username'))">Показать имя пользователя</button>

    <script>
        function setCookie(name, value, days) {
            let date = new Date();
            date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
            let expires = "expires=" + date.toUTCString();
            document.cookie = name + "=" + value + ";" + expires + ";path=/";
        }

        function getCookie(name) {
            let nameEQ = name + "=";
            let ca = document.cookie.split(';');
            for(let i = 0; i < ca.length; i++) {
                let c = ca[i];
                while (c.charAt(0) == ' ') c = c.substring(1, c.length);
                if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length, c.length);
            }
            return null;
        }
    </script>
</body>
</html>
```
