# Мини-банк

Проект "Мини-банк" — middle-сервис, разрабатываемый в рамках обучения GPB IT Factory.

## Архитектура

Приложение состоит из компонентов:
- Frontend. Telegram-бот как килентское приложение;
- Middle. "Мини-банк" - микро-сервис на Java Spring Boot, маршрутизирующий запросы в "Банк";
- Backend. "Банк" - глубинная система, выступающая в качестве автоматизированной банковской системы. 

## Диаграмма взаимодействия

UML-диаграмма последовательности, пример взаимодействия:

```plantuml
actor User

participant FrontTelegram
participant MiddleService
participant BackendSystem

User -> FrontTelegram : Запрос
activate FrontTelegram
    FrontTelegram -> MiddleService : HTTP-запрос
    activate MiddleService
        MiddleService -> BackendSystem : HTTP-запрос
        activate BackendSystem
            BackendSystem -> MiddleService : HTTP-ответ
        deactivate BackendSystem
        MiddleService -> FrontTelegram : HTTP-ответ
    deactivate MiddleService
    FrontTelegram -> User : Ответ
deactivate FrontTelegram
```

## Запуск и пример использования
(Пока тут ничего нет)

## Примечания

<details>
    <summary>UML: типы диаграмм</summary>

- Структурные диаграммы:
  - Диаграмма классов (центральная методика моделирования ООП; описывает классы, их атрибуты, методы и отношения между ними)
  - Диаграмма компонентов (как физические или логические компоненты системы соединяются вместе, зависимости между ними)
  - Диаграмма объектов (показывает экземпляры классов и их связи во время выполнения)
  - Диаграмма развертывания (физическая архитектура системы и размещение компонентов на узлах)
  - Диаграмма пакетов (представление организации и структуры системы в виде пакетов)
  - Диаграмма составной структуры (структура классов в формате диаграммы компонентов)
  - Диаграмма профилей
  
- Диаграммы поведения:
  - Диаграмма прецедентов / вариантов использования (функции системы с точки зрения пользователей, описывает какой функционал доступен каждой группе пользователей)
  - Диаграмма деятельности (оделируют потоки деятельности и последовательности действий)
  - Диаграмма состояний (состояния объекта и переходы между ними)
  - Диаграмма последовательности (жизненный цикл объекта с вертикальными "линиями жизни", отображающими течение времени).
  - Диаграмма коммуникаций (отношения между объектами, последовательность взаимодействий, организованных по времени)
  - Диаграмма обзора взаимодействия (обзор потока упраления между узлами из диаграмм деятельности с последовательностью сообщений между линиями выполнения диаграмм последовательности)
  - Временная диаграмма (схема взаимодействия, основное внимание уделяется временным ограничениям)
</details>

<details>
    <summary>UML: типы связей (отношений)</summary>

  - Ассоциация (Association): --
  - Направленная ассоциация (Directed association): -->
  - Расширение/включение (Extend/Include) -->
  - Агрегация (Aggregation): --<>
  - Композиция (Composition): --<*>
  - Зависимость (Dependency): -.->
  - Мощность (кратность) отношений (Multiplicity): {1}--{0..*}
  - Обобщение/Наследование (Generalization/Inheritance): --*>
  - Реализация (Realization/Implementation): -.-*>

  PlantUML [cheat sheet](https://ogom.github.io/draw_uml/plantuml/)
</details>

<details>
    <summary>Java - первая программа</summary>

```java
/**
 * Программа, выводящая <code>Hello World!</code>
 *
 * @author maks-x32
 * @version 1.0
 */
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```
</details>

<details>
    <summary>Команды для компиляции и запуска Java-кода</summary>

```batch
:: Версия Java, проверка установки
javac -version


:: Узнать откуда запускается Java
where java


:: Компиляция
javac helloworld.java


:: Просмотр байткода в тектовом формате для просмотра глазами
javap -v HelloWorld.class > HelloWorld_classSource.txt


:: Запуск в виртуальной машине (указывается имя класса, а не файла)
:: путь задаётся через -classpath
java HelloWorld
:: (от себя) компиляция и запуск
javac HelloWorld.java && java HelloWorld


:: Формирование архива с классами программы с метаинформацией о программе
jar cfe hw.jar HelloWorld HelloWorld.class


:: Просмотр содержимого архива
jar tf hw.jar


:: Распаковать архив
jar xf hw.jar


:: Запуск программы из jar-архива
java -jar hw.jar
:: (если не прописан главный класс в метаинформации)
java -classpath hw.jar HelloWorld


:: компилятору нужно указывать в classpath где лежат классы-зависимости
javac -classpath lib.jar HelloWorld.java
:: вирт.машине так же нужно знать откуда брать классы-зависимости, нужно добавить их в classpath
java -classpath lib.jar;hw.jar HelloWorld
:: (прим.) в Linux указывается : вместо ;
```
</details>