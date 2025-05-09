# Работа с БД

## Подключение к БД

Для упрощения данного семинара мы не будем подключать postgresql, а будем использовать in memory database - h2
(хранилище в памяти к которому можно обращаться по jdbc и выполнять sql запросы, весьма полезна на студенческих
проектах); в будущем можно будет легко сменить на postgresql, при этом не меняя sql запросы и миграции.

### Doobie

Для работы с БД мы будем использовать библиотеку doobie, которая позволяет нам работать с БД с системой эффектов.

## Миграции

### Создание миграций

1. Создадим папку `src/main/migrations` и подключим её как ресурс в build.sbt -
   `.settings(Compile / unmanagedResourceDirectories += baseDirectory.value / "src" / "main" / "migrations")`;
2. Добавим файл changelog.xml в папку `src/main/migrations`, в нём содержаться перечисление миграций и путь к ним;
3. Добавим папку `src/main/migrations/animal` и создадим 2 файла `animal-create.sql` и `animal-populate.sql`, первый для
   создания таблицы, второй для заполнения данными;

### Запуск миграций

Миграции мы будем накатывать через liquibase.

1. Добавим зависимость `liquibase-core` в `build.sbt`;
2. Добавим код, который будет выполнять
   миграцию [LiquibaseMigration.scala](src/main/scala/tbank/ab/LiquibaseMigration.scala)

### Почему запускать миграции одновременно с приложением плохо?

## Как работать с БД в тестах? (изоляция данных в тестах)
