# Мини-банк (Frontend service)

Проект "Мини-банк" — сервис, разрабатываемый в рамках обучения GPB IT Factory.

В этом репозитории frontend-часть: telegram-бот, принимающий запросы от пользователя и формирующий запросы к MiddleService.

## Общая архитектура проекта

Приложение состоит из компонентов:
- Frontend telegram-бот. Выступает как килентское приложение — **текущий проект**;
- Middle-сервис. "Мини-банк" - микро-сервис на Java Spring Boot, маршрутизирующий запросы в "Банк";
- Backend-сервис. "Банк" - глубинная система, выступающая в качестве автоматизированной банковской системы. 

## Диаграмма взаимодействия

UML-диаграмма последовательности, пример взаимодействия:

```plantuml
actor User

participant TelegramBot
participant MiddleService
participant BackendSystem

User -> TelegramBot : HTTP-запрос
activate TelegramBot
    TelegramBot -> MiddleService : HTTP-запрос
    activate MiddleService
        MiddleService -> BackendSystem : HTTP-запрос
        activate BackendSystem
            BackendSystem -> MiddleService : HTTP-ответ
        deactivate BackendSystem
        MiddleService -> TelegramBot : HTTP-ответ
    deactivate MiddleService
    TelegramBot -> User : HTTP-ответ
deactivate TelegramBot
```

## Запуск и пример использования
(Пока тут ничего нет)
