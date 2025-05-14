# Шаблон docker laravel

## Установка

Собрать сервис workspace:

```bash
docker-compose build workspace
```

Подключится  к сервису workspace и установить laravel:

```bash
docker-compose run --rm workspace bash
```

В контейнере workspace выполнить установку:

```bash
laravel new
```

Далее ответить на все вопросы и установить фреймворк. После переместить все содержимое находясь в папке /var/www

```bash
mv ./laravel/{*,.*} .
```

После перемещения файлов удалить папку проекта внутри /var/www:

```bash
rm -rf ./laravel
```

Выйти из контейнера и собрать контейнер php-fpm:

```bash
docker-compose build php-fpm
```

Далее запустить все сервисы:

```bash
docker-compose up -d
```

Для приложения с базой данных выполнить миграции:

```bash
docker-compose exec workspace php artisan migrate
```
