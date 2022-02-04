# CryptoCurrency_watcher

REST-сервис просмотра котировок криптовалют

REST-методы:

- /api/currencies - просмотр списка доступных криптовалют;

- /api//currencies/{symbol} - просмотр актуальной цены для указаной криптовалюты, 
раз в минуту актуальные цены для доступных криптовалют запрашиваются c внешнего источника - https://www.coinlore.com/cryptocurrency-data-api#3
и сохраняются в базу данных. При запросе актуальной цены для указаной криптовалюты - пользователь получает информацию из базы данных.

- /api/notify - пользователь регистрирует себя, передает свое имя(username) и код криптовалюты(symbol). 
В момент регистрации в базу данных cохраняется текущаю цена указаной криптовалюты с привязкой к пользователю.

Как только актуальная цена для указаной валюты поменялась более чем на 1% (по сравнению с ценой криптовалюты в момент регистрации пользователя), 
в лог сервера выводится сообщение уровня WARN в котором указан: код валюты, имя пользователя и процент изменения цены с момента регистрации.