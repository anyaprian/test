# collect-city-info

## Сервис для поиска и хранения изображений городов и стран. 

Он использует [API Unsplash](https://unsplash.com/developers) для получения изображений и хранит их в Minio (в публичном bucket). Пользователь может отправлять запросы по названию страны и города, после чего сервис проверяет наличие данных в Minio и при отсутствии запрашиваемых изображений отправляет запрос к Unsplash.

---

### API Usage

Авторизация:
Для доступа используется базовая авторизация по ключу, доступному [здесь](https://vault.k8s.faqtrip.com/ui/vault/secrets/collect-city-info/show/deploy/prod/common).

#### 1. Сохранение фото

- **Endpoint:** https://collect-city-info.k8s.faqtrip.com/api/v1/unsplash
- **Method:** POST
- **Request Format:** словарь с полями country и city.

[Пример запроса](https://www.notion.so/faqtrip/Images-collection-8649c410f2f04b5ebf34a4534dec191f?pvs=4#32273ceb1daa4241b987f44fd34def2c)

##### Ответы сервиса:

200 OK: Ответ API сохранен в хранилище.
200 OK: Директория уже существует.
400 Bad Request: Ошибка обработки запроса.
401 Unauthorized: Ошибка авторизации.
500 Internal Server Error: Произошла ошибка при получении данных.


---

### Тестирование и документация

Сваггер сервиса доступен по ссылке: https://collect-city-info.k8s.faqtrip.com/docs

Чтобы протестировать ручки, нужно авторизоваться (кнопка Authorize справа сверху) по [ключу](https://vault.k8s.faqtrip.com/ui/vault/secrets/collect-city-info/show/deploy/dev/common)
