# Counterparty Report

Веб-сервис для проверки контрагентов по ИНН/ОГРН

---

## Стек технологий

- Java 24
- Spring Boot 4.0.6
- Spring Security
- Spring Data JPA
- PostgreSQL 14+
- Maven
- Thymeleaf

---

## Инструкция по запуску

### Шаг 1: Установите Java

Скачайте JDK 21 или 24: https://adoptium.net/

Установите на компьютер

### Шаг 2: Установите PostgreSQL

Скачайте PostgreSQL: https://www.postgresql.org/download/windows/

Установите на компьютер и запомните пароль от пользователя postgres

### Шаг 3: Создайте базу данных

Откройте pgAdmin или командную строку psql

Выполните SQL-запрос:

CREATE DATABASE counterparty_db;

### Шаг 4: Настройте подключение к базе данных

Откройте файл src/main/resources/application.properties

Найдите строки:

spring.datasource.url=jdbc:postgresql://localhost:5432/counterparty_db
spring.datasource.username=postgres
spring.datasource.password=postgres

Измените пароль на ваш пароль от PostgreSQL:

spring.datasource.password=ваш_пароль

### Шаг 5: Настройте токен DaData API

Зарегистрируйтесь на https://dadata.ru и получите API-ключ

В файле src/main/resources/application.properties найдите строку:

dadata.api.token=${DADATA_API_TOKEN}

Замените на ваш реальный токен:

dadata.api.token=ваш_реальный_токен

### Шаг 6: Запустите приложение

Способ 1: Через run.bat

Дважды кликните по файлу run.bat в корне проекта

Способ 2: Через JAR

Откройте командную строку в папке с проектом и выполните:

java -jar target\counterparty-report-0.0.1-SNAPSHOT.jar

Способ 3: Через Maven

mvn spring-boot:run

### Шаг 7: Откройте браузер

Перейдите по адресу: http://localhost:8080

### Шаг 8: Зарегистрируйтесь и войдите

1. Нажмите "Нет аккаунта? Зарегистрироваться"
2. Введите username и password
3. Нажмите "Зарегистрироваться"
4. Введите логин и пароль на странице входа
5. Нажмите "Войти"

---

## Как пользоваться сервисом

### Проверка контрагента

1. На главной странице введите ИНН (10 цифр) или ОГРН (13 или 15 цифр)
2. Нажмите "Проверить"
3. Система отобразит структурированный отчёт с карточкой компании, основными сведениями, адресом, статусом, датой регистрации и кратким резюме

### История проверок

1. Нажмите "История проверок" в меню
2. Вы увидите список всех ваших запросов
3. Нажмите "Посмотреть отчёт" для просмотра сохранённого отчёта

### Статистика

1. Нажмите "Статистика" в меню
2. Вы увидите общее количество проверок, успешных, ненайденных и ошибок

---

## Требования к системе

- JDK 21 или выше (рекомендуется 24)
- PostgreSQL 14+
- Браузер (Chrome, Firefox, Edge)

---

## Возможные проблемы и решения

Проблема: Connection refused
Решение: PostgreSQL не запущен → запустите службу PostgreSQL

Проблема: Password authentication failed
Решение: Неверный пароль → проверьте пароль в application.properties

Проблема: Database "counterparty_db" does not exist
Решение: База не создана → выполните CREATE DATABASE counterparty_db;

Проблема: Компания не найдена
Решение: Проверьте правильность ИНН/ОГРН