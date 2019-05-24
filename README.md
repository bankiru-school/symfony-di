# Symfony Dependency Injection

### Практическое задание по конфигурации контейнера и DI

## Цели

1. Понять принципы построения DI в Symfony
2. Понять процессы происходящие при сборке контейнера

## Задачи

1. Форкнуть и склонировать проект
2. Модифицировать тесты `Tasks/Tests` до позеленения
3. Отправить пулл-реквест с решением задачи
4. Участвовать в обсуждении своего и чужих пулл-реквестов

## Задания

Идентификатор сервиса `not found` используется в качестве проверки несуществующего сервиса 
и не должен быть зарегистрирован в контейнере ни в одном задании

Хорошей практикой является проверка того, может ли ваш `ContainerBuilder` быть сохранен в файловый кэш. 
Для проверки используйте хелпер `Dumper::dump(ContainerBuilder $builder)`

Разрешается изменять и создавать новые только файлы в папке `Tasks/Tests` 
кроме изменения иерархии наследования предсозданных болванок тестов

В качестве идентификатора выполненного задания принимаются зеленые тесты (по версии travis-ci) 
из папки `Tasks/Tests` без измененной иерархии наследования или конфигурации travis

### The box

Использовать только конфигурацию контейнера через код.

1. Собрать пустой контейнер
2. Собрать контейнер, в котором в качестве 
   сервиса `service_container` зарегистрирован инстанс этого самого контейнера
3. Собрать контейнер, инициализирующий сервис `static_counter` класса `StaticCounter` только один раз при получении
4. Собрать контейнер, инициализирующий сервис `static_counter` класса `StaticCounter` каждый раз заново при получении
5. Собрать контейнер, инициализирующий сервис `static_counter` класса `FactoryCounter` только один раз при получении

### The YAML box

1. Выполнить задания The Box 3 сконфигурировав контейнер через YAML
2. Выполнить задания The Box 4 сконфигурировав контейнер через YAML
3. Выполнить задания The Box 5 сконфигурировав контейнер через YAML

### The false bottom

1. Собрать контейнер, инициализирующий контроллер `GreetingController` в сервис `greeting_controller` так, 
   чтобы зависимость `greeter` невозможно было получить через контейнер
2. Соберите контейнер, в котором один и тот же инстанс `greeting_controller` из п. 1 доступен так же 
   по идентификаторам `controller` и `greeting_action`
3. Собрать контейнер со следующими харатектеристиками:
    1. Дано: в контейнере есть сервис `tracker` (`BasicTracker`)
    2. Если в контейнере есть сервис `logger`, то нужно задекорировать `BasicTracker` с помощью `LoggingTracker`
    3. Если в контейнере есть сервис `cache`, то нужно задекорировать `BasicTracker` с помощью `CachingTracker`
    4. Если в контейнере есть и сервис `logger` и сервис `cache`, то нужно наложить сначала логирующий декоратор, а потом кэширующий

### Deal with it

Пара заданий "со звездочкой"

1. Собрать контейнер, инициализирующий сервисы `Circular`: `A`, `B` и `C` 
   с идентификаторами `circular_a`, `circular_b`, `circular_c`
2. Сделать то же самое, без явной настройки зависимостей

### What time is it?

Время компилировать!

1. Сконфигурируйте контейнер так, чтобы сервис `optional_extension` класса `OptionalExtension` был сконфигурирован 
   только в случае наличия сервиса `optional_dependency`. Сервисы добавляются **после** вашей конфигурации 
2. Сконфигурируйте контейнер так, чтобы в реестр `seeker` попали все сервисы с тегом `find_me`

## Материалы

1. [PSR-11](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-11-container.md)
2. [Документация Symfony DI](http://symfony.com/doc/current/components/dependency_injection.html)
3. [Исходный код Symfony DI](https://github.com/symfony/dependency-injection)
4. [Сборка контейнера](http://symfony.com/doc/current/components/dependency_injection/compilation.html)
