WEBSERVICE

WebService - проект, позволяющий с помощью POST запросов решать не сложные математические выражения.

---

**КАК ПОЛЬЗОВАТЬСЯ?**

Для начала скачайте архив с кодом из последнего релиза.
Распакуйте в удобную для вас папку и запустите _терминал_ из нее.
Используя команду

**go run .\main\webservice.go**

вы запустите сервер, и он сможет обрабатыввать ваши запросы.

После этого вы можете, используя curl, обращаться к серверу.
В ответ вы получите результат работы:

1. Ответ на ваше математическое выражение.
2. Ошибку

Чтобы отправить запрос, воспользуйтесь командой

**curl -X POST -H 'Content-Type:application/json' -d '\{\"expression\":\"YOUR_EXPRESSION\"\}' http://localhost:8080/api/v1/calculate**

где **YOUR_EXPRESSION** - ваше выражение

---

ПРИМЕРЫ ИСПОЛЬЗОВАНИЯ.

curl -X POST -H 'Content-Type:application/json' -d '\{\"expression\":\"2+2\*2\"\}' http://localhost:8080/api/v1/calculate

вернет

{"result":"6"}

т. к. выражение задано правильно и других ошибок нет.

curl -X POST -H 'Content-Type:application/json' -d '\{\"expression\":\"+2\*2\"\}' http://localhost:8080/api/v1/calculate

вернет

{"error":"Expression is not valid : simplecalc.Calc(expretion)"}

т. к. выражение составлено не правильно.

curl -X POST -H 'Content-Type:application/json' -d '{"a":"a"}' http://localhost:8080/api/v1/calculate

вернет

{"error":"Internal server error : json.Unmarshal"}

т. к. не передаётся "expression", т. е. программа не может найти ключ к выражению.
