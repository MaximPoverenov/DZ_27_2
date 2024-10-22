Инструкции по запуску команды для установки на Linux:

sudo apt update sudo apt install docker.io sudo systemctl start docker sudo systemctl enable docker sudo apt install docker-compose

Эта команда соберет Docker образы и запустит все сервисы.

Склонируйте репозиторий проекта

Настройка переменных окружения

Запустите сборку и все необходимые сервисы:

docker-compose up --build

Выполнение миграций базы данных:

docker-compose exec django python manage.py migrat

Доступ к приложению:

http://localhost:8000
lesson_24_1

Файл payment_data.json в папке /users/ Для выполнения команды загрузки данных в модель Payment, используйте следующую команду:

python manage.py load_payments

Загрузите начальные данные (опционально): Если в проекте есть фикстуры с начальными данными (например, для групп пользователей), вы можете их загрузить:

python manage.py loaddata users/fixtures/groups.json

API Эндпоинты Аутентификация пользователей Регистрация: POST /api/users/register/ Логин: POST /api/users/login/

JWT Токен Получение токена: POST /api/token/ Обновление токена: POST /api/token/refresh/

API для курсов Список курсов: GET /api/courses/ Создание курса: POST /api/courses/ (Только для администраторов) Получение курса: GET /api/courses/{id}/ Обновление курса: PUT /api/courses/{id}/ (Модераторы могут обновлять) Удаление курса: DELETE /api/courses/{id}/ (Только для администраторов)

API для уроков Список уроков: GET /api/lessons/ Создание урока: POST /api/lessons/ (Только для администраторов) Получение урока: GET /api/lessons/{id}/ Обновление урока: PUT /api/lessons/{id}/ (Модераторы могут обновлять) Удаление урока: DELETE /api/lessons/{id}/ (Только для администраторов)

API для платежей Список платежей: GET /api/payments/ (Только для авторизованных пользователей) Фильтрация платежей по курсу, уроку или способу оплаты: GET /api/payments/?course={course_id}&lesson={lesson_id}&method={method}

Для получения данных с пагинацией можно отправить запрос на /courses/ или /lessons/. Для изменения количества элементов на странице добавьте параметр запроса, например: ?page_size=20
